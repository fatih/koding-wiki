# KDModalViewLoad

KDModalViewLoad is inerhited from
[KDModalView](/framework/modals/KDModalViewLoad). It is exactly the same as with
KDModalView with just some differences. There are two methods you can call after
the modal view get loaded and before the modal view get destroyed. These are

* onLoad
* onBeforeDestroy 

Below is a modifed example of KDModalView code, which shows these methods in
action:

          modal = new KDModalViewLoad
            onLoad: ->
              new KDNotificationView
                title: 'I loaded everything, now I can show the Modal View!'
            onBeforeDestroy: ->
              new KDNotificationView
                title: 'Let me do show this notification before I destroy the Modal View'
            title: "A Modal with a Title"
            content: "Do you want to continue?"
            height: "auto"
            overlay: yes
            buttons:
                Yes:
                    loader:
                        color: "#ffffff"
                        diameter: 16
                    style: "css-class"
                    callback: ->
                        new KDNotificationView
                            title: "Clicked yes!"
                        modal.destroy()
                No:
                    loader:
                        color: "#ffffff"
                        diameter: 16
                    style: "css-class"
                    callback: ->
                        new KDNotificationView
                            title: "Clicked no!"
                        modal.destroy()

