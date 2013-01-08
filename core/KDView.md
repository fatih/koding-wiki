# KDView

KDView is inerhited from [KDObject](/core/KDObject). It's the basic class for
all gui classes in KD Framework. 


The currently supported options are:

* tagName: a String of a HTML tag. By default it is "div".  It defines the basic
  tag for the html view.

* domId: a String. By default it is null.
* cssClass: a String. By default it is empty.
* parent: a KDView Instance. By default it is null. If looks for this variable,
  if not available the view itself is assigned as a parent.

* partial: a String of HTML or text. By default it is null.
* pistachio: a String of Pistachio. By default it is null.
* delegate: a KDView Instance. By default it is null.
* bind: a String of space seperated javascript dom events to be listened on instantiated view. By default it is
* draggable: an Object holding draggable options and/or events !!! NOT HTML5
  !!!. By default it is null.
* droppable: TBDL. By default it is null.
* size: an Object holding width and height properties. By default it is null.
* position: an Object holding top/right/bottom/left properties (would force view to be positioned absolutely). By default it is null.
* attributes: an Object holding attribute key/value pairs e.g. {href:'#',title:'my picture'}. By default it is null.
* prefix: a String. By default it is empty.
* suffix: a String. By default it is empty.
* tooltip: an Object of twipsy options. By default it is null.
