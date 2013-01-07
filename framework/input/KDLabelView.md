# KDLabelView

KDLabelView is a an easy way to create a `<label>` element. Below is an example code:

    :::coffeescript
    inputView = new KDLabelView
      cssClass      : "custom-css-class"
      title         : "This is a label"
      tooltip       :
        title       : "If you hover this label this text will be showed"
      click         : ->
        console.log "If you click on this label, this text will be printed"

Anything here is optional. The `title` option set the dom elements title.
`tooltip` and `click` are standart options that are here just for example
