# KDFormViewWithFields

This method creates a form with fields. Below is an example with three
[fields](link to field doc) (name, domain and email) and two
[KDButtons](/framework/buttons/KDButtonView) (install and cancel). 

    :::coffeescript
    form = new KDFormViewWithFields
      buttons               :
        Install             :
          title             : "Install button"
          style             : "cupid-green"
          type              : "submit"
          loader            :
            color           : "#444444"
            diameter        : 12
          callback          : =>
            new KDNotificationView
                title : "Button clicked"
            form.buttons["Create Rails instance"].hideLoader()
         Cancel             :
           title            : "Cancel"
           style            : "css-class"
           callback          : ->
             new KDNotificationView
               title : "Cancel clicked"
      fields                :
        name                :
          label             : "Put your name here"
          name              : "name"
          placeholder       : "write name here - example placeholder"
          defaultValue      : "ExampleName"
          validate          :
            rules           :
              required      : "yes"
              regExp        : /(^$)|(^[a-z\d]+([a-z\d]+)*$)/i
            messages        :
              required      : "a name for your rails app is required!"
          nextElement       :
            timestamp       :
              name          : "timestamp"
              type          : "hidden"
              defaultValue  : Date.now()
        domain              :
          label             : "Domain :"
          name              : "domain"
          itemClass         : KDSelectBox
          defaultValue      : "#{nickname}.koding.com"
        email       :
          cssClass          : "emailExisting"
          label             : "Username or Email:"
          type              : "hidden"
          nextElement       :
            kodingUser      :
              label         : "Koding User Email"
              type          : "hidden"
