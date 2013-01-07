First Steps
===========

Creating a Koding Application is easy. All you need is inside Koding
development environment. Suprised? :)

First, right click your Applications directory and click **Make a new
Application**.

![image](first_make.png)

This will open a dialog and let you select a template and name for your
application.

![image](first_newapp.png)

Select **Blank Application** and write your first application's name.
Click **Create** and your first application will be created under
**Applications** folder.

![image](first_edit.png)

Double click index.coffee file and write your first Koding application:

    :::coffeescript
    class HelloApp extends KDView
        viewAppended:->
            super

            {nickname} = KD.whoami().profile

            button = new KDButtonView
                title      : "Hello"
                callback   : ->
                    new KDNotificationView
                        title : "Hello #{nickname}!"
            @addSubView button

    do ->
        appInstance = new HelloApp
        appView.addSubView appInstance

Now it's time to compile your application. **Save** it, **Compile** it
and **Run** it! You can find these buttons on the top right corner of
your development environment:

![image](first_compile.png)

Koding will view your application in a new tab, and you'll see your
first application running.

![image](first_view.png)

Now, say **Hello** to the world! This was easy, isn't it?

