# KDHitEnterInputView

KDHitEnterInputView is inerhited from [KDInputView](/framework/input/KDInputView). It
is actually similar to KDInputView, however a callback is called if someone
press enter. Below is a sample code:

    @addSubView hiEnterView = new KDHitEnterInputView
      type      : "text"
      name      : "Hit Enter for Callback"
      callback  : (value) =>
        new KDNotificationView
          content : "You wrote: #{value}"


Because it is inerihted from KDInputView you use most of the options.  Below are
options currently supported (some are different than KDInputView):

* **type:** a String. Defines the type of the input field. By default its a
  `<input>` element of type `textarea`. Rest is same as
  [KDInputView](/framework/input/KDInputView).

## NOT COMPLETED API OPTIONS:

* **button**. a Boolean.

* **showButton** . a Boolean. By default it is no. If set to yes, hitting enter
  will not work (instead)

