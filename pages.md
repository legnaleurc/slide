# Stability Testing in Gecko

Wei-Cheng Pan
(2015/11/25)

# What?

* Recording All Events
* Replay Them Afterward

# Why?

Save the Track for each Test Case

# How?

(in JavaScript)

1. mock **EventTarget.prototype.addEventListener**
2. serialize captured events
3. deserialize events
4. use **EventTarget.prototype.dispatchEvent**

[example](https://github.com/legnaleurc/calc/blob/master/js/event.js#L79)

# Problems

* Targets in an Event
    * target
    * currentTarget
    * relatedTarget
* Recover Target
    * CSS Selector does not always work

# in C++

* Intercept Events in **EventDispatcher::Dispatch**
* Serialize Events and EventTargets
* Deserialize Events and EventTargets
* Create Events by **Event::Create**

# Serialization

* **EventTarget** and **nsPresContext**
* Log an Increamental ID in the constructor
* Convert the Pointer to ID while Saving
* Convert the ID back to Pointer while Loading

# (cont.)

* Add Another Serialization Interface to nsIEvent

# Demo
