# KDSelectBox

KDInputViewWithPreview is inerhited from
[KDInputView](/framework/input/KDInputView).
It's a simple selectbox which you can use on its alone or with KDInputView
itself. Below is an example code:

    :::coffeescript
    chooseFTP : new KDSelectBox
      type          : "select"
      name          : "type"
      defaultValue  : "ftp"
      selectOptions : [
                      { title : "FTP", value : "ftp" }
                      { title : "SFTP", value : "sftp" }
                      ]

There is no spesific additional option. Please refer to
[KDInputView](/framework/input/KDInputView) for more information. 
