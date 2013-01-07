# KDInputValidator

This class is used by various KDInputView classes. It basically validates the
input data from the user. Below is an example used withing KDInputView itself:


    :::coffeescript
    inputView = new KDInputView
      cssClass      : "test-input"
      placeholder   : "Write something to create a notification..."
      validate      :
        event       : "keyup"
        rules       :
          required  : yes
          email     : yes
        messages    :
          required  : "That's a very required field..."
          email     : "Email is invalid..."
        events:
          email     : "keydown"
          required  : "mouseenter"


KDInputView view takes all the rules and chain them into one global validation.
That means you can sum up validations. Like "email + minimum length of 9" or
"maximum length of 10 + regex". There are several validations rules you can
use. Below is the set of rules you can use and is currently supported by us

* **required**: If set to yes, the field is required to be filled.
* **email:**: If set to yes, the field get validated for type of "Email"
* **minLength:** a Number. If set the field should consist of minumum length
of characters 
* **maxLength:** a Number. If set the field should consist of maxiumum
length of characters
* **rangeLength:** an Array of Number. The array has two values, one for
minLength and one for maxLength. Anything beyond this lengths get unvalidated.
* **match:** a Value. If set the field is validate for this value itself. Useful
  to point to another input field and match it against it. Like checking for
  passwords.
* **creditCard**: validate for a creditcard number. If it is validated a
  "CreditCardTypeIdentified" together with the type (Visa, MasterCard, Amex,
  Diners, Discover, JCB) is emitted.
* **JSON**: validate for JSON data
* **uri**: validate for URI, like URL's, paths,etc..
* **regExp**: validate agains a custom regex rule

Besides the rules you add custom error messages for each rule. Also you can 
specify for each validation a custom event (as shown in the example).







