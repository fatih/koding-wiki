#KDOnOffSwitch

KDOnOffSwitch is inerhited from [KDInputView](/framework/input/KDInputView). It is a
simple on-off switch. There is also
[KDInputSwitch](/framework/input/KDInputSwitch), which is similar but doesn't
has a "on" and "off" label on it. Below is an example code:

    :::coffeescript
    onoffSwitch = new KDOnOffSwitch
      defaultValue  : on
      title         : "An On-Off Switch"
      size          : "big"
      cssClass      : "test-switch"
      callback      : (state) ->
        if state
          new KDNotificationView
            content : "Mode: ON"

Some additional options are:

* defaultValue: option can take these parameters: on,"on","true","yes" and 1. If
not is is by defaull off.
* size: a String. By default it is "small". Takes these parameters
    * tiny
    * small
    * big
* labels: an Array of String. By default it is ["ON", "OFF"]. You can override
  it with custom labels
