# Event Recorder in Gecko

Wei-Cheng Pan

performance team in Mozilla Taiwan

2015/12/10

# Why?

<!-- when we doing monkey or fuzz testing -->
monkey/fuzz testing

# Why?

<!-- repeat many times to reproduce again -->
<!-- require a precise gesture/timeing -->
* bugs randomly happen
<!-- it does not works on my machine -->
<!-- a stack dump is not enough -->
* hard to report or share

# What?

<!-- most of time you do not know where is the problem -->
* save the track after execution
<!-- easy to test, easy to cooperate -->
* reproduce it again

# How? (in JavaScript)

1. mock **EventTarget.prototype.addEventListener**
2. serialize captured events

[example](https://github.com/legnaleurc/calc/blob/master/js/event.js#L79)

# How? (in JavaScript)

1. deserialize events
2. use **EventTarget.prototype.dispatchEvent**

[example](https://github.com/legnaleurc/calc/blob/master/js/event.js#L79)

# Problems

<!-- when you get them wrong, the listener won't trigger -->
targets in an `Event`

* `target`
* `currentTarget`
* `relatedTarget`

# Problems

<!-- to do this, I convert the Element back to an unique selector -->
how to serialize all targets?

CSS selector does not always work

# in C++

1. intercept in `mozilla::EventDispatcher::Dispatch`
2. serialize by `nsIEvent::SerializeEvent`

# in C++

1. deserialize by `mozilla::EventDispatcher::CreateEvent`
2. dispatch by `mozilla::EventDispatcher::Dispatch`

# Pointer Serialization

* `EventTarget` and `nsPresContext`
* register an incremental ID in the constructor
* convert the pointer to ID while saving
* convert the ID back to pointer while loading

# Event Serialization

* there are `Serialize`/`Deserialize` in the interface
* add another serialization interface to `nsIEvent`

# Demo
