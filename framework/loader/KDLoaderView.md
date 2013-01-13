#KDLoaderView

KDLoaderView is inerhited from [KDView](/core/KDView). It's a canvas element
that draws a indicator, useful for loading processes. Below is an example code:

    :::coffeescript
    @loader = new KDLoaderView
      size          :
        width       : 16
      loaderOptions :
        color       : "#222222"
        shape       : "spiral"
        diameter    : 16
        density     : 30
        range       : 0.4
        speed       : 1.5
        FPS         : 24

KDLoaderView has by default the `kdloader` css class defined. The currently
supported options are:

* **size:** defines the size of the loader. By default the width and height is set
  to 12. It override the loaderOptions.diameter with the size of width.

* **loaderOptions**

  * **color:** a String (HEX). By default it is "#000".
  * **shape:** a String. By defaul it is "spiral". Defines the smallest unit shape
    of the loader. If the loader is very small in size, than the shape is barely
    visible, thus each type may look like the same. The following types are
    supported:

    * spiral
    * square
    * oval
    * square
    * rect
    * roundRect

  * **diameter:** a Number. By default it is 12. Supported range is 10-200.  Sets
    the diameter of the loader view. Is overrided by the option `size`.
  * **density:** a Number. By default it is 30. Supported range is 5-160.  Sets the
    density of the loader units. The larger the number, the slower the loader
    due the number of units available on the screen.
  * **range:** a Number. By default it is 0.4. Supported range is 0.1. - 2. Defines
    the units occupieng the circle. 1 means the whole circle is occupied with
    the loader units. You have to experiment with this value to archieve the
    your desired look.
  * **speed:** a Number. By default it is 1.5. Supported range is 1-10. Sets the
    speed of the loader.
  * **FPS:** a Number. By default it is 24. Supported range is 1-60. Sets the frames
    per screen of the loader. You can archieve different effects combined
    together with the speed option.

There are two methods which sets the current status of the loader view:

* **show:** if used the loader is activated.
* **hide:** if used the loader is deactivated.

KDLoaderView is a widely used component. Below is an example code to test out
all the options. It launches the loader after you clich the "Start the loader!"
button. After 5 seconds it dissapers. Have fun!:

    :::coffeescript
    class LoaderExample extends JView
      constructor:->
        super
        @button = new KDButtonView
          title: "Start the loader!"
          callback: =>
            @loader.show()
            KD.utils.wait 5000, =>
              @loader.hide()
        
        @loader = new KDLoaderView
          size          :
            width       : 100
          loaderOptions :
            color       : "#222222"
            shape       : "roundRect"
            diameter    : 16
            density     : 50
            range       : 0.4
            speed       : 1.5
            FPS         : 24

      pistachio:->
        """
        {{> @button}}
        {{> @loader}}
        """
      viewAppended: ->
        @setTemplate do @pistachio

    appView.addSubView new LoaderExample


## Easter Egg:

If you hower the mouse on the loader, the speed is lowered and a random color is
applied to the loader.


  
