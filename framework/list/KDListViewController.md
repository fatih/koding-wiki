# KDListViewController

KDListViewController is inerhited from
[KDViewController](/core/KDViewController). It let you create easily lists with
custom items. By custom we mean any view that is [KDView](/core/KDView) related.

The constructor takes two arguments:

  constructor:(options = {}, data)

Where options is a object of the following are currently supperted

* **wrapper**             ?= yes
* **scrollView**          ?= yes
* **keyNav**              ?= no
* **multipleSelection**   ?= no
* **selection**           ?= yes
* **startWithLazyLoader** ?= no
* **itemChildClass**     or= null
* **itemChildOptions**   or= {}
* **view**: a KDListView. If empty than the foloowing 

      viewOptions                  = options.viewOptions or {}
      viewOptions.lastToFirst      or= options.lastToFirst
      viewOptions.itemClass        or= options.itemClass
      viewOptions.itemChildClass   or= options.itemChildClass
      viewOptions.itemChildOptions or= options.itemChildOptions

      @setListView listView = new KDListView viewOptions





    if options.view
      @setListView listView = options.view
    else
      viewOptions                  = options.viewOptions or {}
      viewOptions.lastToFirst      or= options.lastToFirst
      viewOptions.itemClass        or= options.itemClass
      viewOptions.itemChildClass   or= options.itemChildClass
      viewOptions.itemChildOptions or= options.itemChildOptions

      @setListView listView = new KDListView viewOptions

    if options.scrollView
      @scrollView = new KDScrollView
        lazyLoadThreshold : options.lazyLoadThreshold
        ownScrollBars     : options.ownScrollBars

    if options.wrapper
      options.view = new KDView cssClass : "listview-wrapper"
    else
      options.view = listView

Below is an example code:

    @listController = new KDListViewController
      lastToFirst     : yes
      viewOptions     :
        type          : "example-list"
        itemClass     : ExampleListItem

Where ExampleListItem is of type
[KDListItemView](/framework/list/KDListItemView).

KDListViewController is a common component which is used a lot.  Below is an
example app that shows the basic of a KDListViewController together with a
KDListItemView. 

class MainView extends JView
  constructor:->
    super
    @header = new KDHeaderView
      type: "big"
      title: "Example for KDListViewController and KDListView"

    @listController = new KDListViewController
      lastToFirst     : yes
      viewOptions     :
        type          : "example-list"
        itemClass     : ExampleItemView
        
    @listView = @listController.getView()

    @buttons = new KDButtonGroupView
      buttons: 
        "Add Item"  :
          callback    : =>
            input = @inputView.getValue()
            @listController.addItem input
            @_notify?.destroy()
            @_notify = new KDNotificationView
              title : "Item added!"
        "Remove Item" :
          callback    : =>
            input = @inputView.getValue()
            itemView = @listController.getListView()
            console.log itemView
            @listController.removeItem itemView.items, input
            @_notify?.destroy()
            @_notify = new KDNotificationView
              title : "Item removed!"
        "Remove all Items"  :
          callback    : =>
            @listController.removeAllItems()
            @_notify?.destroy()
            @_notify = new KDNotificationView
              title : "All items removed"
              
    # Get item name
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
  constructor: (options, @data) ->
    super
    
  partial: (data)-> 
    """
    #{data}
    """

appView.addSubView new MainView
  cssClass: "my-koding-app"
