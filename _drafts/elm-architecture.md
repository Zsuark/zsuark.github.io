# The Model View Presenter Pattern

The Model View Presenter (MVP) is a design pattern for... 

reactive functional programming

...similar to Model View Controller (MVC)....

# A word on the MVC pattern

My preference to MVC is to have heavier models and lighter controllers - i.e. domain logic is contained within the model, and the controller holds the control flow logic. Side note: notice how many implementations have light models &mdash; often just Object-Relational mappers, and heavy controllers. IMHO this makes code re-use more difficult, and fails to separate domain logic from flow-control well.

# Elm

Elm uses 



https://medium.com/@maxf/things-i-wish-i-knew-about-elm-when-i-started-b0ba5bd8438e

"Your CSS and HTML are written in code (see the view function above). It looks declarative (YAML-ish) but is indeed code." - Err... YAML is code!