#KDTabViewWithForms

KDTabViewWithForms is inerhited from [KDTabView](/framework/tab/KDTabView). 

* **sanitizeOptions:(options)->**
* **handleClicked:(index,event)=>**
* **createTabs:(forms)->**
* **createForm:(formData,parentTab)->**
* **getFinalData:->**
* **fireFinalCallback:->**

Example code:

    :::coffeescript
    new KDTabViewWithForms
      callback              : (formOutput)-> log formOutput,"All Forms ::::::"
      navigable          : yes
      forms                 :
        "My first form"     :
          buttons           :
            Next            :
              title         : "Next"
              style         : "modal-clean-gray"
              type          : "submit"
          # callback          : (formOutput)-> log formOutput,"Form 1 ::::::"
          fields            :
            Hiko            :
              label         : "Title:"
              type          : "text"
              name          : "hiko"
              placeholder   : "give a name to your topic..."
              validate      :
                rules       :
                  required  : yes
                messages    :
                  required  : "topic name is required!"
            Zikko           :
              label         : "Zikkko"
              type          : "textarea"
              name          : "zikko"
              placeholder   : "give something else to your topic..."
              nextElement   :
                lulu        :
                  type        : "text"
                  name        : "lulu"
                  placeholder : "lulu..."
        "My Second Form"    :
          buttons           :
            Submit          :
              title         : "Submit"
              style         : "modal-clean-gray"
              type          : "submit"
            Reset           :
              title         : "Reset"
              style         : "modal-clean-red"
              type          : "reset"
          # callback          : (formOutput)-> log formOutput,"Form 2 ::::::"
          fields            :
            Hoho            :
              label         : "Hoho:"
              type          : "text"
              name          : "title"
              placeholder   : "give a gogo..."
              validate      :
                rules       :
                  required  : yes
                messages    :
                  required  : "topic name is required!"
