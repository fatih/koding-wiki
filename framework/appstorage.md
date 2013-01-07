# App Storage

AppStorage helps you keep key-value pairs in a NOSQL database.

    :::coffeescript
    appStorage = new AppStorage "storage-name", "1.0"
    appStorage.fetchValue "names", (names) ->
        names or= []
        new KDNotificationView
            title : "Total: " + names.length

    :::coffeescript
    appStorage = new AppStorage "storage-name", "1.0"
    appStorage.fetchValue "names", (names) ->
        names or= []
        names.push "username1"
    appStorage.setValue "names", names
