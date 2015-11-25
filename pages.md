# Stability Testing in Gecko

Wei-Cheng Pan
(2015/11/25)

# What?

* Record Necessary Events
* Replay Them Afterward

# Why?

Sometimes We Can't Always Get the Same Result in a Test Case

Save the Track after Execution, and Reproduce It Again

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

* Intercept Events in **mozilla::EventDispatcher::Dispatch**
* Serialize Events
* Deserialize Events
* Create Events by **mozilla::EventDispatcher::CreateEvent**

# Pointer Serialization

* **EventTarget** and **nsPresContext**
* Log an Incremental ID in the Constructor
* Convert the Pointer to ID while Saving
* Convert the ID back to Pointer while Loading

# Event Serialization

* There is Another **Serialize**/**Deserialize** in the Interface
* Add Another Serialization Interface to nsIEvent

# Demo
