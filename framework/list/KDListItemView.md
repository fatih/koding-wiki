# KDListItemView

KKDListItemView is inerhited from [KDView](/core/KDView).

It used by [KDListView](/framework/list/KDListView) for setting the default item
instance view. It is the "view" part of the "list" family, where the "modal" is
[KDListView](/framework/list/KDListView) and the "controller" is
[KDListViewController](/framework/list/KDListViewController).

The constructor takes two arguments:

    :::coffeescript
    constructor:(options = {}, data)

## options

The following options are supported:

* **type**: a String. By default it is set to: "default". It used for overriding
  the default css class of KDListView. By default KDListItemView's css class is
  set to "kdlistitemview kdlistitemview-#{options.type}". As you see if you
  change the type, to, say "foo", than the class will be change to:
  "kdlistitemview kdlistitemview-foo"

* **cssClass**: a String. By default it is empty. If a string is assigned than
  it get added to the predefined css classes (as seen above when explaining
  type)

* **bind**: a String of space seperated javascript dom events to be listened
  on instantiated view. By default it has the following events assigned:
  "mouseenter", "mouseleave".

* **childClass**: a KDView. By default it is null. If specified than the
  "option" argument is `childOptions`, where "data" is passed direclty from the
  KDListItemView getData() method. If not defined, then a custom partial with
  the following content is set:

    :::html
    <div class='kdlistitemview-default-content'>
      <p>This is a default partial of <b>KDListItemView</b>,
      you need to override this partial to have your custom content here.</p>
    </div>

* **childOptions**: an Object. Passed to the custom "childClass" constructors as
  the "option" argument, where "data" is passed direclty from the KDListItemView
  getData() method.

