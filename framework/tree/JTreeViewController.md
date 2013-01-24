# JTreeViewController

JTreeViewController is inerhited from
[KDViewController](/core/KDViewController). It let you create easily tree views
with custom items (our file tree is written with this class!)

# options

* **view**: a KDView. By default its a KDScrollView 
* **listViewControllerClass**: a KDView based on KDViewController. By default it
  is a KDListViewController.
* **treeItemClass**: a KDView based on KDListItemView. By default it is a
  JTreeItemView.
* **listViewClass**: a KDView based on KDItemView. By default is is JTreeView.
* **itemChildClass**: a KDView class. This is used to define the item class of
  the listViewClass defined above. By default it is empty.
* **itemChildOptions**: an Object. This is passed as the "options" parameter to
  the `itemChildClass` defined above. By default it is an empty object.
* **nodeIdPath**: a String. By default it is set to "id".
* **nodeParentIdPath**: a String. By default it set to "parentId"
* **contextMenu**: a Boolean. By default is disabled. If enabled listens to the
  mouse event and calls the method  `contextMenu` (which is a good place to
  create a context menu, i.g clicking right click)
* **multipleSelection**: a Boolean. By default it is disabled. If enabled, one
  is able to select multiple items.
* **addListsCollapsed**: a Boolean. By default it is disabled. If enabled all
  the tree nodes expands recursively.
* **sortable**: a Boolean. By default it is disabled. Not implemented yet.
* **putDepthInfo**: a Boolean. By default it is disabled. If enabled assigned the
  depth of each node to the `nodeData.depth` variable.
* **addOrphansToRoot**: a Boolean. By default it is enabled. This changes the
  parent id path to "0". TODO
* **dragdrop**: a Boolean. By default it is disabled. If enabled assignes the
  "draggable" attribute to the nodeView.
