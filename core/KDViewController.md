# KDViewController

KDViewController is inerhited from [KDController](/core/KDController). It's
basically a KDObject with additional basic methods. These basic methods forms
the template for some other important view controllers, such as
[KDListViewController](/framework/list/KDListViewController).

The default constructor calls the @setView method (explained below) to set the
main view of the view controller. The constructor by default check for the
`option.view` object, if it exist the `@setView @getOptions().view` is called.
If there is no `option` parameter passed than @setView is not called.

The methods supported are:

* **loadView(mainView)**:

An empty method that needs to be implemented. This method is called by
`setView()`, which sets the mainView to the paramater given in `setView`.


* **setView(aViewInstance)**:

Sets the @mainView to the given `aViewInstance` view object. It also calls the
following command:

    :::coffeescript
    @loadView.bind(@, aViewInstance)

which binds the object itself to the `aViewInstance` view. This means the object
itself is handled via `aViewInstance`.

* **getView**:

Returns the @mainView, which is assigned in `setView` (see above)


