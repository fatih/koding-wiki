# KDInputViewWithPreview

KDInputViewWithPreview is inerhited from [KDInputView](/framework/kdinputview).
It is a textarea input with two views. One for input the other for preview of
the content. By default the input content is excepted as "markdown". Thus the
preview view shows a markdown formatted view of the input. Below is an example
code:

    discussionBody = new KDInputViewWithPreview
      preview         : 
        autoUpdate    : no
        mirrorScroll  : yes
      showHelperModal : no
      cssClass        : "discussion-body"
      name            : "body"
      title           : "your Discussion Topic"
      type            : "textarea"
      placeholder     : "What do you want to contribute to the discussion?"


Because it is inerhited from KDInputView below is only options that are spesific
to KDInputViewWithPreview:

* **preview.autoUpdate**: a Boolean. By default it is yes. Update the preview view
  automatically.
* **preview.language**: a String. By default it is "markdown". Defines the
  language of the markup language to be used in the preview view. Currently
  there is only support for markdown.
* **preview.showInitially**: a Boolean. By default it is yes. Enable or disable
  the preview view at initial view.
* **preview.mirrorScroll**: a Boolean. By default it is yes. Synchronize the
  current status of the cursor with the preview view.
* **allowMaximized**: a Boolean. By default it is yes. Enables the user to open
  a fullscreen mode. This puts the input area and the preview view next to next.
* **showHelperModal** a Boolean. By default it is yes. Shows a link to modal
  view which shows useful markdown syntax documentation.


