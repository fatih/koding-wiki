# KDNotificationView

KDNotificationView is an easy way to inform with different styles of
notifications. It is useful for any warning, error or if you have finished
something and want to inform the user. Below is an example:

    :::coffeescript
    inputView = new KDNotificationView
      title         : "This is a warning!"
      duration      : 1500
      type          : "mini"


Below are several options currently supported:

* **type:** a String. Defines the type of the notification. By default its of type
  **main**. The current options are:
      * main
      * tray
      * mini
      * growl

* **title:** a String. By default it is empty. Defines the title of notification (if
  you prefer one.)

* **content:** a String. By default it is empty. Defines the content of
  notification. This one should be set and shouldnt be empty.

* **duration:** a Number. By default it is 1500 msec. The notification will
  dissappear after 1500 mseconds. If you set this to a number over 2999 or 0
  then `closeManually` is enabled.

* **showTimer:** a Boolean. By default it is disabled. Shows a timer in seconds which is
  counting down.

* **overlay:** a Boolean. By default is is disabled. If enabled the notification
  get destroyed if clicked outside the notification area. Otherwise it doesn't
  get destroyed.


This is a useful class which you want to use a lot. Below is an example single
app to try all of them:

    :::coffeescript
    class NotificationExample extends KDView

      viewAppended: ->
        super

        @addSubView header = new KDHeaderView type : "big", title : "KD Notifications Demo"
      
        buttonNotification = new KDButtonView
          title       : "Show a Notification"
          callback    : ()->
            new KDNotificationView
              type    : "main"
              title   : "Yesss"
              content : "Something weird happened"
              duration: 0
              overlay : yes
              
        buttonNotificationMini = new KDButtonView
          title       : "Mini Notification"
          callback    : ()->
            new KDNotificationView
              type    : "mini"
              title   : "Yes."
              content : "This is a mini notification"
              duration: 0
              overlay : yes
              
        buttonNotificationTray = new KDButtonView
          title       : "Tray Notification"
          callback    : ()->
            new KDNotificationView
              type    : "tray"
              title   : "Hey!"
              content : "This is a tray notification"
      
        buttonNotificationGrowl = new KDButtonView
          title       : "Growl Notification"
          callback    : ()->
            new KDNotificationView
              type      : "growl"
              title     : "Helloo!"
              content   : "This is like growl notification"
              duration  : 10000
              showTimer : yes

        @addSubView buttonNotification
        @addSubView buttonNotificationMini
        @addSubView buttonNotificationTray
        @addSubView buttonNotificationGrowl
      
    do ->
      appInstance = new NotificationExample
     
      # appView is a constant that you can use as your app container
      appView.addSubView appInstance

