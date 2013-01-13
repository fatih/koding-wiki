#KDImage

This component has methods to proccess and do certain task on images. Below are
the currently supported methods:

## Static methods

  * dataURItoBlob: This is a static method to convert a Data URI to a Blob. This
    blob can be then appended to a FormData for further usage. Below is an
    example that creates a Data URL to be used with dataURItoBlob. After that
    you can convert it to a Object URL.  You can use this URL (objectURL) as the
    src attribute for an `<iframe> / <img>` element.

        :::coffeescript
        dataURL = canvas.toDataURL('image/png')
        blob = KDImage.dataURItoBlob dataURL
        objectURL = URL.createObjectURL blob

    For more info about the usage of dataURItoBlob, please have a look at here:
    [Convert Data URI to File then append to FormData](http://stackoverflow.com/questions/4998908/convert-data-uri-to-file-then-append-to-formdata)

## Instance methods:

These methods are used as an instance method. To do this you have to first
create new KDImage class. Below is an example of this:

    :::coffeescript
    imgExample = new KDImage(file)

The constructor takes two arguments:

* **data** : The file 
* **format**: a String. Takes two arguments, which the second depends on the
  first argument.By default it is 'image/png'. It is the type of the image
  format (defaults to PNG). Chrome supports the 'image/webp' type.  If the
  requested type is 'image/jpeg' or 'image/webp', then the second argument, if
  it is between 0.0 and 1.0, is treated as indicating image quality; if the
  second argument is anything else, the default value for image quality is used.
  Other arguments are ignored.

After creating an new KDImage(like imgExample), you can use the following
methods via `imgExample.toBlob()`, `imgExample.createView()`, etc:

* **toBlob():** calls dataURItoBlob for the data given by the constructor.
* **load (src, callback)**:
* **process (action, algorithm)**: 
* **processAll (action, callback)**: 
* **createView()**: 

