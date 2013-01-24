# KDListView

KDListView is inerhited from [KDView](/core/KDView). It used by
[KDListViewController](/framework/list/KDListViewController) for setting the
@listView inside the controller. It is the "modal" part of the "list" family,
where the "view" is KDListItemView and the "controller" is KDListViewController.

The view class itself is handled via the [KDListItemView](KDListItemView). It
looks for the "viewOptions.itemClass" option. Whenever the method "addItem" of
KDListView is called(which is done by
[KDListViewController](/framework/list/KDListViewController)) the variable
"itemClass" is checked for existing. If it exists than the itemInstance is set
to this class, if there is no "itemClass" than the class for the item itself is
set to [KDListItemView](/framework/list/KDListItemView). There is an example
Koding app with sample code on the
at[KDListViewController](/framework/list/KDListViewController) class which shows
this in action.

The constructor takes two arguments:

    :::coffeescript
    constructor:(options = {}, data)

An internal `@items` array is declared, which is by default empty (if not
overrided). This array stores all item instances. The methods, that will be
explained below are all based on modification of this internal array. Thus if I
say "it is iterating over @items", than it means I'm mentioning this array.

The following options are supported:

* **type**: a String. By default it is set to: "default". It used for overriding
  the default css class of KDListView. By default KDListView's css class is set
  to "kdlistview kdlistview-#{options.type}". As you see if you change the type,
  to, say "foo", than the class will be change to: "kdlistview
  kdlistview-foo"

* **lastToFirst**: a Boolean. By default it is disabled. If enabled the items
  are populated in reverse order.

* **cssClass**: a String. By default it is empty. If a string is assigned than
  it get added to the predefined css classes (as seen above when explaining
  type)

The following methods are methods:

* **empty:**

Empty the array `@items`. It is iterating over `@items` and is destroying each
existing item. After that the `@items` is set to an empty array.

* **keyDown:(event)**

Emit's the event "KeyDownOnList". This is catched by the KDListViewController to
handle the selection of items inside the KDListView.

* **addItem:(itemData, index, animation)**

Add `itemData` to the `@item` array. This is calling this wrapper:

    :::coffeescript
    @addItemView itemInstance, index, animation

where `itemInstance` is a [KDListItemView](/framework/list/KDListItemView).
If you provide any index (second argument), then the item is added into this
spesific index, if not, it is appended to the end of the list (reminder: __the
item is added to the beginning of the array if `options.lastToFirst` is enabled
in the KDListView constructor__).

If you provide any animation (third argument) than the item is added via this
animation. `animation` is defined like:

    :::coffeescript
    animation = type : "fadeIn/fadeOut", duration : 500 # in msecs

This is a handled via jQuery, thus have a look at jQuery documentation for
effects:
[http://api.jquery.com/category/effects/](http://api.jquery.com/category/effects/)

* **addHiddenItem:(item, index, animation)**

It's basically the same as `addItem` except that following options are applied
to the item instance (which is a
[KDListItemView](/framework/list/KDListItemView)).

    :::coffeescript
    viewOptions :
      isHidden  : yes
      cssClass  : 'hidden-item'

* **addItemView:(itemInstance,index,animation)**

If used, an event named `ItemWasAdded` is emitted too. Add `itemInstance` to the
`@items` array. The `index` and `animation` are explained in the `addItem`
method. It's calling the following wrapper if index is available:

    :::coffeescript
    @appendItemAtIndex itemInstance, index, animation

if index is not available the following wrapper method is called:

    :::coffeescript
    @appendItem itemInstance, animation

* **removeItem:(itemInstance, itemData, index)**

It takes three arguments. These are :

  * itemInstance: the item view 
  * itemData: the item data 
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

Finally the 'ItemIsBeingDestroyed' event is emitted.
