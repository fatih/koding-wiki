# KDListViewController

KDListViewController is inerhited from
[KDViewController](/core/KDViewController). It let you create easily lists with
custom items. By custom we mean any view that is [KDView](/core/KDView) related.

The constructor takes two arguments:

    :::coffeescript
    constructor:(options = {}, data)

Where options is a object of the following are currently supperted:

* **wrapper**: a Boolean. By default it is yes. It sets `options.view` to a new
  KDView class with a css class of name: "listview-wrapper". That means you can use
  getView() (which comes from KDViewController) to get a ready view for your
  list. If you set it to `no`, then the listView is set to `options.view`.
* **scrollView**: Boolean. By default it is yes. The listView is added as a
  subView to a KDScrollView. If you don't want this you can disable it.
* **keyNav**: Boolean. By default it is no. If enabled, listview is listening to
  a "KeyDownOnList" event, which fires the keyDownPerformed function for the
  listView itself.
* **selection**: Boolean. By default it is yes. Listens to "click" event.
  KDListViewController will callback the function @selectItem with the view and
  event.
* **multipleSelection**: Boolean. By default it is no.  It basically select the
  items trough multiple selections. This is done automatically via the methods
  below. If enabled listens to "mousedown" and "mouseenter" events. Which if
  caught calls the following
  methods:
    * for "mousedown" - > @mouseDownHappenedOnItem view, event
    * for "mouseenter" - > @mouseEnterHappenedOnItem view, event

* **startWithLazyLoader**: By default it is no. If enabled shows a
  [KDLoader](/framework/loader/KDLoader) with a "Loading..." partial text. The
  loader should be then deactivated or activated manually trough te
  showLazyLoader() and hideLazyLoader() functions.
* **itemChildClass**: an item Instance. By default it is null. However most of time
  you want might modify it. Usually this option is set via the sub-option
  `viewOptions`. We have KDListItemView class that you might extend and use for
  this.
* **itemChildOptions**: an Object. By default it is empty. This is needed if you
  want pass options to the child class (look above). 
* **view**: 

KDListViewController has many useful methods to modify or change any behaviour of
a controller. Below are the currently supported methods:

## helpers

* **itemForId**:(id)

Get the item view for the `id` number. This returns the object
`@itemsIndexed[id]`, which is by default empty. But if we add an item to the
list, than the controller stores the id together with the view. This is done
automatically via the controller.

* **getItemsOrdered**:

Get itemsOrdered variable. This variable is an array which contains all our
views.

* **getItemCount**:

Get the length of itemsOrdered. This gives as the total number of items
currently available in our list.

* **setListView**:(listView)

Sets the listView for our controller. By default the constructor 
is creating a view that is provided via options.view. If you don't set
options.view, then a new KDListView is created with `options.viewOptions`
provided. However you can use this method manually and create set your own
listView.

* **getListView**:

Returns the listView.

* **forEachItemByIndex**:(ids, callback)

Returns each item for the `ids` array. This array should contain id's. This is
actually the same as `itemForId`, but it iterates over the `ids` array and call
back the items.

## modifications

* **addItem**:(itemData, index, animation)

Add itemData (modal) to the view. This is a wrapper that calls 

    :::coffeescript
    @getListView().addItem itemData, index, animation

Where getListView() method is described above. Because our listView is a
KDListView, it calls actually KDListView.addItem(). It takes three arguments,
however you can omit the second and third argument.

If you add any Item, than a 'ItemWasAdded' event is emitted via KDListView. If
you provide any index (second argument), then the item is added into this
spesific index, if not, it is appended to the end of the list (reminder: __the
item is added to the beginning of the array if `options.lastToFirst` is enabled
in the KDListViewController constructor__).

If you provide any animation (third argument) than the item is added via this
animation. `animation` is defined like:

    :::coffeescript
    animation = type : "fadeIn/fadeOut", duration : 500 # in msecs

This is a handled via jQuery, thus have a look at jQuery documentation for
effects:
[http://api.jquery.com/category/effects/](http://api.jquery.com/category/effects/)

* **removeItem**:(itemInstance, itemData, index)

Removes the item from the list. This is a wrapper that calls 

    :::coffeescript
    @getListView().removeItem itemInstance, itemData, index

Just like addItem(), this calls actually KDListView.removeItem(). It takes three
arguments. These are :

  * itemInstance: the item view (instance)
  * itemData: the item data (is: item.getData())
  * index: the index of the list

Each one is optional. It means you have three methods to remove an item from a
list. You can just give the item view (instance) itself. The method will try to
itarate over all existing items and removes the first one it matches.

    :::coffeescript
    @removeItem itemInstance

The secon option is to give a `itemData`. This is like the above, however it
matches the data of the item instance instead of the item as a whole:

    :::coffeescript
    @removeItem null, itemData

Finally you can just give the an index number. This will remove an item if it
exist at that index. If your index number is out of bound than nothing will be
done:

    :::coffeescript
    @removeItem null, null, index

Because the usage of removeItem above seems so awkward, we have two wrappers for
this arguments, one for removing item by data and another one to remove by
index (THIS ARE NOT IN USAGE CURRENTL, PENDING ...):

    :::coffeescript
    removeItemByData:(itemData)->
      @removeItem null, itemData

or

    :::coffeescript
    removeItemByIndex:(index)->
      @removeItem null, null, index

* **registerItem**:(view, index)

What means registering? For every item added to the list a 'ItemWasAdded' event
is emitted. Our controller catched this and calls the `registerItem()` method.
The registerItem method takes two arguments. `view` is the item instance and `index`
is used to populate itemsOrdered array. Basically, this method is called
automatically every time you use the `addItem()` method. It is updating the
internal arrays and variables of the controller itself.

This method is useful if you want use anything different than KDListView. You
might implement your own ListView class and emit the 'ItemWasAdded'.
KDListViewController will listen to this event and register the view for
yourself. 

* **unregisterItem**:(itemInfo)

Just as the same as registerItem(). For every item removed from the list a
'ItemIsBeingDestroyed' event is emitted. Our controller cathes this and calls
the `unregisterItem().` This removes the view and data from the internal
itemsOrdered and itemsIndexed variables. itemInfo is an object of view and
index. Which can be accessed like:

    :::coffeescript
    {index, view} = itemInfo

* **replaceAllItems**:(items)

Replace the list with the `items` data. This method calls first removeAllItems()
and then iterates over the `items` array to add all the items in it. 

* **removeAllItems**:

Removes all items from the list. This reset itemsOrdered and itemsIndexed
variables. 

## item selection

* **selectItem**:(item, event = {})->

This function is used by the internal controller. It is used to return the
selected items. For example if use the method `selectNextItem` (with an argument
of a specific item), then the next item will be selected and returned. This is
done by this function (`selectItem`). This uses internally the
`selectSingleItem` method, whereupon this method propagates the
"ItemSelectionPerformed" event.

* **selectItemBelowOrAbove**:(event)->

This is internally used by the controller, which acts on the events `down`
and `up`. After selecting the items `selectSingleItem` is performed on the
items.

* **selectNextItem**:(item, event)->

Return the next item of the passed `item` argument. It uses `selectItem`
internally.  The method `selectSingleItem` is performed on all item.

* **selectPrevItem**:(item, event)->

Return the previous item of the passed `item` argument. It uses `selectItem`
internally. The method `selectSingleItem` is performed on the item.

* **deselectAllItems**:()->

Removes all the selections (it clears the `selectedItems` array).

* **deselectSingleItem**:(item)->

Deselect the `item` passed.

* **selectSingleItem**:(item)->

Selects a single `item`, unless it is not already selected. If it is not
selected then a this `item` is added to the `selectedItems` array. The `item` is
highlighted and the method `itemSelectionPerformed()` is called.

* **selectAllItems**:()->

Select all items. The method `selectSingleItem` is called on all items.

* **selectItemsByRange**:(item1, item2)->

Select all items between `item1` and `item2`. The method `selectSingleItem` is
than performed on all the items selected and finally the method
`itemSelectionPerformed` is called.

* **itemSelectionPerformed**:->

Propagates the `ItemSelectionPerformed` event, together with an object of 

    event : @lastEvent
    items : @selectedItems

* **itemDeselectionPerformed**:(deselectedItems)->

Propagates the `ItemDeselectionPerformed` event, together with an object of 

    event : @lastEvent
    items : deselectedItems

## lazy loaders

* **showLazyLoader**:(emitWhenReached = yes)->

If startWithLazyLoader is enabled, this method is used to show the loader. This
method is used when ever you want to show the loader again after hiding the
loader via `hideLazyLoader()` method. By default the variable `emitWhenReached`
is set to yes, which propagates the event 'LazyLoadThresholdReached'.

* **hideLazyLoader**:->

If startWithLazyLoader is enabled, this method is used to hide the loader.

# Example app for KDListViewController and KDListItemView

KDListViewController is a common component which is used a lot.  Below is an
example app that shows the basic of a KDListViewController and KDListItemView.
The app looks like:

![image](KDList.png)

In the picture you see that we have alreayd added three items. The code for this
app is:

    :::coffeescript
    class MainView extends JView
      constructor:->
        super
        @header = new KDHeaderView
          type: "big"
          title: "Example for KDListViewController and KDListView"
          
        @listController = new KDListViewController
          lastToFirst         : yes
          startWithLazyLoader : yes
          viewOptions         :
            type              : "example-list"
            itemClass         : ExampleItemView
            
        @listView = @listController.getView()
        
        @buttons = new KDButtonGroupView
          buttons:
            "Add Item"  :
              callback    : =>
                input = @inputView.getValue()
                @listController.addItem input
                @listController.hideLazyLoader()
                @_notify?.destroy()
                @_notify = new KDNotificationView
                  title : "Item added!"
            "Remove Item" :
              callback    : =>
                inputData = @inputView.getValue()
                @listController.removeItem null, inputData, null
                @_notify?.destroy()
                @_notify = new KDNotificationView
                  title : "Item removed!"
            "Remove all Items"  :  
              callback    : =>
                @listController.removeAllItems()
                @listController.showLazyLoader()
                @_notify?.destroy()
                @_notify = new KDNotificationView
                  title : "All items removed"
                  
        @inputView = new KDInputView
          cssClass      : "test-input"
          placeholder   : "Write item name..."

      pistachio:->
        """
        {{> @header}}
        {{> @inputView}}
        {{> @buttons}}
        {{> @listView}}
        
        """
      viewAppended: ->
        @setTemplate do @pistachio
        
    class ExampleItemView extends KDListItemView
      constructor: (options, data) ->
        super
        
      partial: =>
        content = @getData()
        """
        #{content}
        """
    
    appView.addSubView new MainView
      cssClass: "my-koding-app"

Let me explain the code in detail. The code itself is looks like a lot, however
it's mostly the button and callback part that takes so much space. Anyway as you
see we created a KDListViewController which is the main controller for our
KDListItemView's:

    :::coffeescript
    @listController = new KDListViewController
      lastToFirst     : yes
      viewOptions     :
        type          : "example-list"
        itemClass     : ExampleItemView

As you see we use here `viewOptions` to define our item class. We use our own
item class, named `ExampleItemView`. If we don't define anything then
an empty KDListItemView with no options is applied. You can remove the itemClass
option and compile the app to see the result:

![image](KDList2.png)

Ok, why is this showing? Because prior of this we were overriding the `partial`
of the KDListItemView. We do these in the line:

    :::coffeescript
    @listController.addItem input

The `@listController.addItem input` line basically creates a new list item based
on the itemClass. The `addItem()` method is described at the beginning of the,
basically here `input` is the first argument. If we ommit any other arguments,
than coffeescript assumes these as `null`. This means the line above is the same
as:

    :::coffeescript
    @listController.addItem input, null, null

Now if we use `ExampleItemView` for the options `itemClass` than the partial is
overrided via our own extended class:

    :::coffeescript
    class ExampleItemView extends KDListItemView
      constructor: (options, data) ->
        super

      partial: =>
        content = @getData()
        """
        #{content}
        """

As you here see, we're getting the data and showing it in the `partial`. We are
overriding `partial. That's it because we use our custom KDListItemView
(`ExampleItemView`) and setting it to `itemClass` in KDListViewController.

Now, there are actually three ways to remove(as explained at the beginning). We
used the second way. The code for this is:

    :::coffeescript
    inputData = @inputView.getValue()
    @listController.removeItem null, inputData, null

Because we didn't give any index number or item instance, we are iterating over
the whole list array until we match `inputData`. This is done automatically via
`removeItem()`. Now this seems very easy, however problems occur when you have
an item that is of complex form. Be careful with that. Another way is to remove
via item instances, like:

    :::coffeescript
    itemView = @listController.getListView()
    @listController.removeItem itemView.items[2], null, null

This will remove the third item instance in the list. 

You will probably notice the loader which is starting to load if there is no
items. This is so because we set the `startWithLazyLoader` option to `yes` in
the constructor of the KDListViewController:

    :::coffeescript
    @listController = new KDListViewController
      lastToFirst         : yes
      startWithLazyLoader : yes
      ...

However as you notice the loader dissapear when add any item and appear again if
remove all items. This is done manually with the following methods in the add
item and removeAllItems button states:

    :::coffeescript
    # in "Add Item" button callback:
    @listController.hideLazyLoader()

    # in "Remove all Items" button callback:
    @listController.showLazyLoader()
