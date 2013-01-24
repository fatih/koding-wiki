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
  parent id path to "0".
* **dragdrop**: a Boolean. By default it is disabled. If enabled assignes the
  "draggable" attribute to the nodeView.

## helpers

**initTree:(nodes)->**:
**logTreeStructure:->**
**getNodeId:(nodeData)->**
**getNodePId:(nodeData)->**
**repairIds:(nodeData)->**
**isNodeVisible:(nodeView)->**
**areSibling:(node1, node2)->**

## decorators

**setFocusState:->**
**setBlurState:->**

## crud operations for nodes

**addNode:(nodeData, index)->**
**addNodes:(nodes)->**
**removeNode:(id)->**
**removeNodeView:(nodeView)->**
**removeAllNodes:->**
**removeChildNodes:(id)->**
**nodeWasAdded:(nodeView)->**
**getChildNodes :(aParentNode)->**
**addIndexedNode:(nodeData)->**
**removeIndexedNode:(nodeData)->**

## creating lists

**registerListData:(node)->**
**createList:(listId, listItems)->**
**addSubList:(nodeView, id)->**

## registering listeners

**setMainListeners:->**
**setListenersForList:(listId)->**
**setItemListeners:(view, index)->**

## node selection

**organizeSelectedNodes:(listController, nodes, event = {})->**
**deselectNodes:(listController, nodes, event)->**
**deselectAllNodes:(exceptThisController)->**
**selectNode:(nodeView, event, setFocus = yes)->**
**deselectNode:(nodeView, event)->**
**selectFirstNode:->**
**selectNodesByRange:(node1, node2)->**

## collapse / expand

**toggle:(nodeView)->**
**expand:(nodeView)->**
**collapse:(nodeView)->**

## dnd ui feedbacks

**showDragOverFeedback: do ->**
**clearDragOverFeedback: do ->**
**clearAllDragFeedback: ->**

## handling mouse events

**mouseEventHappened:(nodeView, event)->**
**dblClick:(nodeView, event)->**
**click:(nodeView, event)->**
**contextMenu:(nodeView, event)->**
**mouseDown:(nodeView, event)->**
**mouseUp:(event)->**
**mouseEnter:(nodeView, event)->**

## handling dnd

**dragStart: (nodeView, event)->**
**dragEnter: (nodeView, event)->**
**dragLeave: (nodeView, event)->**
**dragOver: (nodeView, event)->**
**dragEnd: (nodeView, event)->**
**drop: (nodeView, event)->**

## handling key events

**setKeyView:->**
**keyEventHappened:(event)->**
**performDownKey:(nodeView, event)->**
**performUpKey:(nodeView, event)->**
**performRightKey:(nodeView, event)->**
**performLeftKey:(nodeView, event)->**
**performBackspaceKey:(nodeView, event)->**
**performEnterKey:(nodeView, event)->**
**performEscapeKey:(nodeView, event)->**
