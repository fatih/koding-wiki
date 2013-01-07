#KDInputSwitch

KDInputSwitch is inerhited from [KDInputView](/framework/kdinputview). It is a
simple on-off switch. There is also [KDOnOffSwitch](/framework/kdonoffswitch),
which is similar but has a "on" and "off" labels on it. KDInputSwitch is more
general and useful if you want just let users enable certain things. Below is an
example code:

    :::coffeescript
    inputSwitch = new KDInputSwitch
      defaultValue  : on
      cssClass      : "test-switch"
      callback      : (state) ->
        if state
          new KDNotificationView
            content : "Mode: ON"

* defaultValue option can take these parameters: on,"on","true","yes" and 1. If
not is is by defaull off.
