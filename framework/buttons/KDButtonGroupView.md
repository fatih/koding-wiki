# KDButtonGroupView

KDButtonGroupView is inerhited from [KDView](/framework/core/KDView). It
let you group buttons in an easy way. Below is an example code:
   
    :::coffeescript
    buttonGroup = new KDButtonGroupView
      buttons: 
        "first button"  :
            loader      :
                color   : "#444444"
                diameter: 12
            callback    : ->
                new KDNotificationView
                    content : "You clicked the first button!"
        "second button" :
            callback    : ->
                new KDNotificationView
                    content : "You clicked the second button!"

Each button is a [KDButtonView](/framework/buttons/KDButtonView).  Thus you can
add loaders, style the buttons, etc..
