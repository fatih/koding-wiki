#KDHeaderView

KDHeaderView is inerhited from [KDView](/core/KDView). It let you create HTML
headings (`<h1>`, `<h2>`, etc..). However up to `<h4>` is supported.
KDHeaderView has by default the `kdview` and `kdheaderview` css classes defined.
Below is an example code:

    :::coffeescript
    @header = new KDHeaderView
      type: "big"
      title: "Koding is fun!"

You can the heading type with the following options:

* **type**: a String. By default it is set to `<h4>`. There are three types that you
  can use:

    * **big** : if set the tag is set to `<h1>`
    * **medium** :if set the tag is set to `<h2>`
    * **small** : if set the tag is set to `<h3>`

* **title** : This sets the content of the headings. The title is wrapped around
  a `<span>` tag before it get appended to the DOM element.


