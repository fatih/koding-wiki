# KDInputView

KDInputView is a an easy way to create various input fields. By default it
creates an `<input>` html element of type **text**. However you also can use
`<select>` or `<textarea>`.  Below is an example code:

    :::coffeescript
    inputView = new KDInputView
      cssClass      : "test-input"
      placeholder   : "Write something to create a notification..."
      validate      :
        event       : "keyup"
        rules       :
          required  : yes
        messages    :
          required  : "That's a very required field..."

In this example the following options are used:

* cssClass
* placeholder
* validate

Some options are neglected because they have pre defined default values. However
KDInputView has more options and it's very customizable. Below are the options
currently supported:

* **type:** a String. Defines the type of the input field. By default its a `<input>` element of type `text`. The current options are:
    * `"text"`      (creates a `<input>` element of type `text`)
    * `"password"`  (creates a `<input>` element of type `password`)
    * `"hidden"`    (creates a `<input>` element of type `hidden`)
    * `"checkbox"`  (creates a `<input>` element of type `checkbox`)
    * `"range"`     (creates a `<input>` element of type `range`)
    * `"textarea"`  (creates a `<textarea>` html element)
    * `"select"`    (creates a `<select>` html element)

* **name:** a String. It defines the name attribute of the input element. By default it is empty.
* **label:** a KDLabelView instance. For more info look at the [KDLabelView](/framework/kdlabelview) doc.
* **cssClass:** a String. It defines the class attribute of the input element. By
  default it is empty. However koding has some default css classes that you can
  use. KDInputView comes default with the `kdinput` css class. For more info
  look at [Css Template Classes](/framework/css_clasess)
* **callback:** a Function. By default it is null. Usefull if you want to call a
  function from the function itself.
* **defaultValue:** a String or a Boolean value depending on type. By default it is
  empty. It sets the value of the input element to a given default value.
* **placeholder:** a String. By default it is empty. Set the input text area to this
  string. Useful if you want users guide for an input type (like :
  foo@example.com). Here the user know that he should enter an email address.
* **disabled:** a Boolean value.By default it is set to no. Makes the text field disabled.
* **selectOptions:** an Array of Strings. By default it is null. This is used to set
  options if you have choosed the type of the KDInputView as `select`.
* **validate:** an Object of Validation options see
  [KDInputValidator](/framework/kdinputvalidator) for details. By default it is
  null.  Useful if you want validate the input for certain cases (like email,
  underscore, etc..)
* **validationNotifications:** a Boolean. By default it is yes. If disabled it
  doesnt show a mini [KDNotificationView](/framework/KDNotificationView) for
  validation errors (see validate)
* **autogrow:** a Boolean. By default it is no. If enabled let the input input field
  to be grown if it get filled.
* **bind:** a String of event names. By default "blur change focus" are added. 
* **forceCase:** a String of either "lowercase" or "uppercase". Make the input value
  to uppercase or lowercase.
