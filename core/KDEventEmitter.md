# KDEventEmitter

Many objects in KD Framework emit events: a KDFormView emits an event if the
input validation passed , a KDInputValidator emits an event if the credit card
get validated, a KDTabView emits an event if we select a tab, an so on.. There
are many KD classes that emits events.  All KD Objects which emit events are
instances of KDEventEmitter. 

KDEventEmitter provide a basic skeleton for KDObject and KDView, which lots of
gui elements of KD Framework depends on. Because each KD Class is inerhited from
this class you don't need to declare any new classess. All KD classes are by
default an eventEmitter therefore.

Event names in KD Framework are represented by a camel-cased string, however,
there aren't any strict restrictions on that. Any string will be accepted.

Functions can then be attached to objects, to be executed when an event is
emitted. These functions are called **listeners**. That means you have several
listeners and for each listener an event is associated. 

To handle communication between events and listeners, KDEventEmitter provides
several methods. These methods are used to call the listeners, modify the
listeners array, etc. Below are the methods you can use:

* **emitter.on event, listener **: adds a listener together with the specified event to the end of the
  listeners array (i.e. @button.on "DeleteLinkClicked", (ItemToBeDeleted)). Now
  if someone emit this 'DeleteLinkClicked' event, than this listener will be
  called. 

* **emitter.once event, listener** : just like **on** however adds a one time listener for the event. This
  listener is called just one time, after that it is removed (which actually
  calls the **unsubscribe** method below to run the action)

* **emitter.off event **: reset the listener array so no event will be propagated to previously
  registered listener callbacks. Means if you emit any event, these events will
  be discarded because the listener array is reseted. There you have to add new
  listener via "on" method.

* **emitter.emit event, args **: sent an event, in which every listener get called. This means if you
  sent an event (i.e: @form.emit 'ExampleEmit', @), than every listener in the
  listener array get called with the supplied argument. Above the argument '@'
  (the object itself) is supplied. Here any listener that has the event
  'ExampleEmit' is called with our supplied argument.

* **emitter.unsubscribe event, listener **: removes the given listener for the specifed event.





