# KDButtonViewWithMenu

KDButtonViewWithMenu is inerhited from [KDInputView](/framework/input/KDButtonView). It provides a second menu next to the button. Below is an example code:

    :::coffeescript
    class MainView extends JView
      constructor:->
        super
        
        @saveButton = new KDButtonViewWithMenu
          title         : "Save"
          menu          : @additionalMenu.bind @
          callback      : () =>
            new KDNotificationView
                content : "You saved the World!"
                
      additionalMenu : ->
         "Save as..."  :
              callback  : ->
                  new KDNotificationView
                      content : "Clicked on save as ..."
          "Second button"  :
              callback  : ->
                  new KDNotificationView
                      content : "Clicked on second button ..."
        
      pistachio:->
        """
        {{> @saveButton}}
        """

      viewAppended: ->
        @setTemplate do @pistachio

    appView.addSubView new MainView

Additional informations:

* **iconOnly**: a Bolean. By default it is off. If enabled the text will be not
shown. i.e. in the example code below the text "Save" will not be showed if this
is enabled
* **iconClass**: a String. By default it is off. Needed to define the icon image.

If clicked on the menu, a "ContextMenuItemReceivedClick" signal is emitted. This
signal is created by
[contextmenutreeviewcontroller](/framework/misc/contextmenutreeviewcontroller)


