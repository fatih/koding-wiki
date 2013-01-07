# Running Shell Commands

Koding provides an interface([kite](/backand/kites)) to execute shell commands.

    :::coffeescript
    kc = KD.getSingleton "kiteController"
    kc.run "date", (err, res) ->
        new KDNotificationView
            title : res
