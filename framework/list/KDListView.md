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
Katoding app with sample code on the
at[KDListViewController](/framework/list/KDListViewController) class which shows
this in action.

The constructor takes two arguments:

    :::coffeescript
    constructor:(options = {}, data)

The following options are supported:

* **type**: 
* **lastToFirst**: 
* **cssClass**: 

THe following methods are methods:

* **empty:**
* **keyDown:(event)**
* **addHiddenItem:(item, index, animation)**
* **addItem:(itemData, index, animation)**
* **addItemView:(itemInstance,index,animation)**
* **appendItem:(itemInstance, animation)**
* **appendItemAtIndex:(itemInstance,index,animation)**
* **removeItem:(itemInstance, itemData, index)**
* **destroy:(animated = no, animationType = "slideUp", duration = 100)**
