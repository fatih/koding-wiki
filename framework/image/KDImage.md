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

    Another example:

        "<img src='#{URL.createObjectURL KDImage.dataURItoBlob screenshot.thumb}'/>"

    For more info about the usage of dataURItoBlob, please have a look at here:
    [Convert Data URI to File then append to FormData](http://stackoverflow.com/questions/4998908/convert-data-uri-to-file-then-append-to-formdata)

## Instance methods:

These methods are used as an instance method. To do this you have to first
create new KDImage class. Below is an example of this:

    :::coffeescript
    imgExample = new KDImage(file)

The constructor takes actually two arguments. We ommited the second argument
(takes the default one). The two arguments are:

* **data** : The file 
* **format**: a String. By default it is 'image/png'. Defines the type of the
  image format. For now it is passed to the method `toDataURL.` For more info
  about types you can use please have look at
  [HTMLCanvasElement](https://developer.mozilla.org/en-US/docs/DOM/HTMLCanvasElement)

After creating an new KDImage(like imgExample), you can use the following
methods via `imgExample.toBlob()`, `imgExample.createView()`, etc:

* **toBlob():** calls dataURItoBlob for the data given by the constructor.
* **load (src, callback)**: Creates a new HTML Image element with the src
  containing the URL of the image. After the load of the document the callback
  returns the img element itself.
* **process (action, algorithm)**: Currently can scale and crop images. TODO
* **processAll (action, callback)**: Process all actions specified for the image
  in a queue. TODO
* **createView()**:  Creates a `<img src=...>` element with src pointing to data
  passed in the constructor. If the `data` is a string then it is assigned
  direclty, otherise data.src is assigned.

