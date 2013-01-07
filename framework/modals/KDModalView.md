# Modal Windows

    :::coffeescript 
    modal = new KDModalView
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
