# KDView

KDView is inerhited from [KDObject](/core/KDObject). It's the basic class for
all gui classes in KD Framework. 

---

TODO: Add detailed explanation of KDView, such as how to views are interacting,
viewAppended, addSubView, Pistachio, KDEventEmitter,etc..

EXTRA NOTE: viewAppended is automatically called everytime a view is added to
KDView. If you don't override it in any subclass then it calles the parents
viewAppended method. It's a virtual method, means it is optional. JView (which
is inerhited from KDView) override it in this way:

    :::coffeescript
    class JView extends KDView
      
      viewAppended:->

        @setTemplate @pistachio()
        @template.update()

      pistachio:-> ""

This means that the view is using pistachio as the template engine.

---

Below is an example code to create a KDView:

    :::coffeescript
    class ExampleView extends KDView
      constructor:->
        super
        @header = new KDHeaderView
          type: "big"
          title: "This is a header"

        @addSubView @header

    appView.addSubView new ExampleView
      cssClass: "your-app-name"


appView is a closure function that let us add views to the Application View Dom.
Here we are adding ExampleView to the DOM and defining the css class we are
usign for this view. You can override or setup lots of options for a KDView. The
best way to do this in the constructor itself. Below is an another example that
shows how to do this:

    :::coffeescript
    class ExampleView2 extends KDView

      constructor: (options = {}, data) ->
        
        options.cssClass = "your-app-name"
        options.domID = "spesific-app"
        
        super options, data
        
        @header = new KDHeaderView
          type: "big"
          title: "This is a header"
          
        @addSubView @header
        
    appView.addSubView new ExampleView2

There are several options to customize KDView. Below a are the currently
supported options:

* tagName: a String of a HTML tag. By default it is "div".  It defines the basic
  name for the element. The default value "div" is already a common name for
  adding structure to documents.
* domId: a String. By default it is null. Defines the elements identifier name.
  Ref: [http://www.w3.org/TR/1999/REC-html401-19991224/struct/global.html#adef-id](http://www.w3.org/TR/1999/REC-html401-19991224/struct/global.html#adef-id)
* cssClass: a String. By default it is empty. Defines the class attribute of an
  element. KDView has by default a class with the name "kdview". If you assigned anything
  to to cssClass variable it get appended to kdview instead of overriding it.
  Ref: [http://www.w3.org/TR/1999/REC-html401-19991224/struct/global.html#adef-class](http://www.w3.org/TR/1999/REC-html401-19991224/struct/global.html#adef-class)
* parent: a KDView Instance. By default it is null. If looks for this variable,
  if not available the view itself is assigned as a parent. Means parent is
  always assigned automatically.
* partial: a String of HTML or text. By default it is null. This is useful to
  add any partial html or text inside our dom element. For example :
            
          a  = new KDView
          a.setPartial "<h1>Arslan</h1>"
          # output: <div class='kdview'><h1>Arslan</h1></div>

* pistachio: a String of Pistachio. By default it is null. If used than
  Pistachio template engine is used instead of manually adding views. If you use
  [JView](/core/JView) then then pistachio is enabled by default and you don't
  need to specify it in viewAppended. Below is an example(@header is a
  KDHeaderView, @name is a KDInputView , all defined in contructor of the JView):

        pistachio:->
          """
          {{> @header}}
          Just change something from the left pane.
          <br><br>
          <strong>And try some interactions!:</strong>
          {{> @name}}
          """

* delegate: a KDView Instance. By default it is null.

* bind: a String of space seperated javascript dom events to be listened on
  instantiated view. By default it is empty. However we have some default events
  we're listening too:

        "mousedown mouseup click dblclick paste"

  Any event you are adding will be added to this list.
  
* draggable: an Object holding draggable options and/or events !!! NOT HTML5
  !!!. By default it is null.
* droppable: TBDL. By default it is null.

* size: an Object holding width and height properties. By default it is null.
* position: an Object holding top/right/bottom/left properties (would force view
  to be positioned absolutely). By default it is null.
* attributes: an Object holding attribute key/value pairs e.g.
  {href:'#',title:'my picture'}. By default it is null.
* prefix: a String. By default it is empty.
* suffix: a String. By default it is empty.


notes:

