---
layout:   post
title:    "Quil Tutorial"
date:     2018-02-22 17:30:00 +0100
category: animation
tags:     ["software", "software development", "drawing", "animation", "Clojure", "Quil"]
---

# Quil Tutorial

This is a presentation that I am giving today
to the [Budapest Clojure Users Group](https://www.meetup.com/Budapest-Clojure-User-Group)

- Review my original post: [Front-end Architecture Patterns: Quil](/architecture/2018/02/01/Quil/)
- [The Quil API](http://quil.info/api)
- [Quil Cheatsheet](https://github.com/astanin/clojure-quil/blob/master/docs/cheatsheet/cheat-sheet.pdf)

# Geometry of the screen
 - Screen dimensions & locations

# Skeleton of a Quil drawing

## Start A new Clojure project

From the command line: `lein new empty quil-drawing`


## Edit your project.clj
```clojure
(defproject quil-drawing "0.1.0-SNAPSHOT"
  :description "A Clojure Quil project"
  :dependencies [[org.clojure/clojure "1.8.0"]
                 [quil "2.6.0"]]
  :main quil-drawing.core)
```

# Sample core.clj

Edit the file:
  __`quil-drawing/src/quil_drawing/core.clj`__

```clojure
(ns quil-drawing.core
  (:require [quil.core :as q]))


(defn setup []
  "
  Setup function
  - only called once
  "
  (q/background 0))

#_ (defn update []
     "
     Update function
     - Called before draw
     - Updates state for drawing
     "
     nil)

(defn draw []
  "
  draw function
  - executed for side-effects
  - draws frame onto the screen
  "  
  (q/stroke
    (rand-int 256)
    (rand-int 256)
    (rand-int 256))
  
  (let [width  (q/width)
        height (q/height)]

    (q/line
      (rand-int width)
      (rand-int height)
      (rand-int width)
      (rand-int height))))


(defn -main [& args]
  (q/sketch
    :title         "Quil Drawing Tutorial"
    :size          [500 300]
    :setup         setup
    :draw          draw))
```



## Optional step - use functonal mode

Functional mode
```clojure
(ns quil-drawing.functional
  (:require [quil.core :as q]
            [quil.middleware :as m]))

...

(defn -main [& args]
  (q/sketch
    :title         "Quil Drawing Tutorial"
    :size          [500 300]
    :setup         setup
    :draw          draw
    :features      [m/fun-mode]))
```


# Basic drawing elements

## Control elements

- `background` fills the screen with given background colour
- `stroke` controls colour of line
- `fill` is the fill colour of the shape
- colours can be specified in decimal in order: red, green and blue
- or in hex - just prepend with 0xff
  - 0x - indicates hexadecimal
  - ff - 100% opacity
  - So 100% blue would be: `0xff0000ff`

## 2D Drawing Primitives

- `point`
- `line`
- `rect`
- `quad`
- `triangle`
- `ellipse`
- `arc`

There are also 3D primitives, however I do not cover them in this tutorial. [Check them out in the API documentation](http://quil.info/api/shape/3d-primitives).


# Looping

- The `setup` function is called once
- The `draw` function is called repeatedly to draw each frame to the screen
- The `update` function is called before `draw` to update state
- Use `frame-rate` to set the number of frames per second (fps)
- The fps can be queried with `current-frame-rate`
- To create a static image call `(q/no-loop)`
  - this stops the Quil sketch from calling `draw` repeatedly


# Challenge 1

Write your own sketch that uses a different primitive drawing element other than line.

# Challenge 2

The sample sketch draws multiple drawing elemts over each other.

Change the sketch so that:
  - It only draws one shape at a time
  - A new frame is drawn ever &frac12; second

# Other important functions

- with-translation
- with-rotation
- atom state functions

# H-Tree Fractal

## Update project.clj

```clojure
(defproject quil-drawing "0.1.0-SNAPSHOT"
  :description "A Clojure project"
  :dependencies [[org.clojure/clojure "1.8.0"]
                 [quil "2.6.0"]
                 [org.clojure/math.numeric-tower "0.0.4"]]
  :main quil-drawing.h-tree)
```

## The code

A space-filling line fractal

```clojure
(ns quil-drawing.h-tree
  (:require [quil.core :as q]
            [quil.middleware :as m]
            [clojure.math.numeric-tower :as maths]))

(defonce sWidth  800)
(defonce sHeight (maths/round (/ sWidth (maths/sqrt 2))))

(defonce centre-point
  (vector
    (maths/round (/  sWidth 2))
    (maths/round (/ sHeight 2))))

(def find-line-length
  "
  Finds the line length for iteration i
  given an available width
  
  Where both i and width are non-negative
  integers
  "
  (memoize
    (fn [i width]
      (if (zero? i)
        (/ width 4)
        (/
          (find-line-length (dec i) width)
          (maths/sqrt 2))))))


(def initial-state
  {:iteration     0
   :line-length   0
   :target-length (maths/round
                    (find-line-length
                      0
                      sWidth))
   :points        (list centre-point)
   :width         sWidth
   :paused        false
   :pause-frames  (* 6 24)})

(defn setup []
  ; (q/frame-rate 24)
  (q/stroke 0xffa8d0db)
  initial-state)

(defn update-points [state]
  "
  Replaces each point in the point vector
  with 2 new points
  
  The new points are formed by adding and
  substracting the target length to the point
  
  During odd iterations we add/subtract to
  the horizontal (x)
  
  During even iterations, we add/subtract to
  the vertical (y)  
  "
  (let [target         (:target-length state)
        iteration      (:iteration     state)
        new-points-fn  (fn [acc [x y]]
                         (into
                           acc
                           (if (odd? iteration)
                             (vector 
                               [(+ x target) y]
                               [(- x target) y])
                             (vector
                               [x (+ y target)]
                               [x (- y target)]))))
        
        old-points  (:points state)
        new-points  (reduce new-points-fn (vector) old-points)
        ]
    (assoc state :points new-points)))



(defn update-state [state]
  "
  If the line length less than the target
  then we increment the line length by 1
  
  Otherwise:
  - we increment the iteration
  - we set length to be 0
  - we update the target length with
  the rounded results of our formula
  - we replace the points array with
  the new set of points
  
  However, we can only see lines of 1,
  so lets stop at that point
  "
  
  (let [length (:line-length   state)
        target (:target-length state)]
    (if (< length target)
      
      (update state :line-length inc)
      
      (let [i      (:iteration state)
            next-i (inc i)
            width  (:width state)
            target (maths/round
                     (find-line-length
                       next-i
                       width))]
        (if (zero? target)
          (if (zero? (:pause-frames state))
            initial-state
            (->
              (update state :pause-frames dec)
              (assoc :paused true)))
          
          (->
            (assoc state :iteration next-i)
            (assoc :line-length 0)
            (update-points)
            (assoc :target-length target)))))))


(defn draw-state [state]
  (if (zero? (:iteration state))
    (q/background 0xff2b4570))
  
  (if (not (:paused state))
    (let [points    (:points      state)
          length    (:line-length state)
          iteration (:iteration   state)
          rotation  (if
                      (even? iteration)
                      0
                      (/ q/PI 2))]
      (doseq [[x y] points]
        (q/with-translation
          [x y]
          (q/with-rotation
            [rotation]
            (q/line 0 0 length 0)
            (q/line 0 0 (- length) 0)))))))




(defn -main
  [& args]
  (q/sketch
    :title "H-Tree Fractal"
    :size [sWidth sHeight]
    :setup setup
    :update #'update-state
    :draw #'draw-state
    :middleware [m/fun-mode]))
```