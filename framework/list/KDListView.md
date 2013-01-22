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
overrided). This array stores all item instance. The methods explained below are
all based on modification of this internal array. Thus if I say "it is iterating
over @items", than it means I'm mentioning this array.

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

THe following methods are methods:

* **empty:**

Empty the array `@items`. It is iterating over `@items` and is destroying each
existing item. After that the `@items` is set to an empty array.

* **keyDown:(event)**

Emit's the event "KeyDownOnList". This is catched by the KDListViewController to
handle the selection of items inside the KDListView.

* **addHiddenItem:(item, index, animation)**
* **addItem:(itemData, index, animation)**
* **addItemView:(itemInstance,index,animation)**
* **appendItem:(itemInstance, animation)**
* **appendItemAtIndex:(itemInstance,index,animation)**
* **removeItem:(itemInstance, itemData, index)**
* **destroy:(animated = no, animationType = "slideUp", duration = 100)**
