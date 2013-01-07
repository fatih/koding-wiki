# KDButton

    :::coffeescript
    button = new KDButtonView
        title      : "Hello"
        callback   : ->
            new KDNotificationView
                title : "Hello World!"

If one clicks on the button then the callback is executed. In the
example we show a little notification. We can also add a loader that
spins all the time (useful to show a running action):

    :::coffeescript
    button = new KDButtonView
        title      : "Hello"
        loader            :
          color           : "#444444"
          diameter        : 12
        callback   : ->
            new KDNotificationView
                title : "Hello World!"

    KD.utils.wait 200, =>
        button.hideLoader()

Because we use a loader (which means a small loader will be running that
runs all the time), we have to hide it later. After 200msec we hide it.
Just remove the line with the hideLoader and compile it again. You'll
see that the loader will not stop. The loader is optional.

You can style your buttons:

    :::coffeescript
    button = new KDButtonView
        title      : "Hello"
        style      : "cupid-green"
        callback   : ->
            new KDNotificationView
                title : "Hello World!"

Here a green button will appear. There are several styles by default.
These are currently:

-   small-gray
-   small-blue
-   clean-gray (neutral)
-   clean-red (usefull for No, Logout, Cancel)
-   cupid-green (usefull for Ok, Login, Run)
-   transparent

You can always use your own style. It's all up to you.
