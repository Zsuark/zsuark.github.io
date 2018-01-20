https://proandroiddev.com/taming-state-in-android-with-elm-architecture-and-kotlin-part-1-566caae0f706


reactive functional programming


# The Model View Presenter Pattern

The Model View Presenter (MVP) is a design pattern for... 

https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93presenter

...similar to Model View Controller (MVC)....

# A word on the MVC pattern

My preference to MVC is to have heavier models and lighter controllers - i.e. domain logic is contained within the model, and the controller holds the control flow logic. Side note: notice how many implementations have light models &mdash; often just Object-Relational mappers, and heavy controllers. IMHO this makes code re-use more difficult, and fails to separate domain logic from flow-control well.

I think of Martin Fowler when I think about heavy models

# Elm

Elm uses 

https://www.gitbook.com/book/evancz/an-introduction-to-elm/details

https://guide.elm-lang.org/architecture/


https://medium.com/@maxf/things-i-wish-i-knew-about-elm-when-i-started-b0ba5bd8438e

"Your CSS and HTML are written in code (see the view function above). It looks declarative (YAML-ish) but is indeed code." - Err... YAML is code! Declarative programming is still programming code!