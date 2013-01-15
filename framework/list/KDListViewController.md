# KDListViewController

KDListViewController is inerhited from
[KDListViewController](/core/KDViewController). It let you create easily lists with
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

    if options.view
      @setListView listView = options.view
    else
      viewOptions                  = options.viewOptions or {}
      viewOptions.lastToFirst      or= options.lastToFirst
      viewOptions.itemClass        or= options.itemClass
      viewOptions.itemChildClass   or= options.itemChildClass
      viewOptions.itemChildOptions or= options.itemChildOptions

      @setListView listView = new KDListView viewOptions


Below is an example code:

    @listController = new KDListViewController
      lastToFirst     : yes
      viewOptions     :
        type          : "example-list"
        itemClass     : ExampleListItem

Where ExampleListItem is of type
[KDListItemView](/framework/list/KDListItemView).

KDListViewController is a common component which is used a lot.  Below is an
example app that shows the basic of a KDListViewController and KDListItemView.
The app looks like:

![image](KDList.png)

Here you see that we have alreayd added thre items. The code for this app is:

    :::coffeescript
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
                @listController.removeItem itemView.items input
                @_notify?.destroy()
                @_notify = new KDNotificationView
                  title : "Item removed!"
            "Remove all Items"  :
              callback    : =>
                @listController.removeAllItems()
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

 The `@listController.addItem input` line basically creates a new list item
 based on the itemClass. The `addItem()` method is described at the beginning of
 the, basically here `input` is saved to the internal "data" variable.
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

Now, there are actually two ways to remove(as explaind at the beginning). We
used the second way. The code for this is:

    :::coffeescript
    inputData = @inputView.getValue()
    itemView = @listController.getListView()
    @listController.removeItem itemView.items, inputData

Here only the last two lines are important. First to remove any item we need the
the views. `getListView()` gives us all the content we need to make any
modification. After that we are passing two arguments, `itemView.items`
and `inputData`. Because we didn't give any index number, we are iterating over
the whole list array until we match `inputData`. This is done automatically via
`removeItem()`. Now this seems very easy, however problems occur when you have
an item that is of complex form. Be careful with that. Another way is to remove
via indexes, like:

    :::coffeescript
    itemView = @listController.getListView()
    @listController.removeItem itemView.items[2]

This will remove the third item in the list.
