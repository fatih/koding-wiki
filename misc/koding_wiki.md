# How to contribute and deploy Koding Wiki?

This wiki is based on simple, markdown powered engine called **markdoc**. The
best part about **markdoc** is that there are no db or any fancy input forms.
Just bare plain markdown files. 

## How to create(deploy) the Wiki?

We use `markdoc` to generate static files(install it via `pip install markdoc`
). These are useful if we want to serve them. But you can always serve the whole
wiki from your own machine with the following command(in the koding-wiki folder):

    markdoc build 
    markdoc serve

Now you can read all the docs on you localhost via
[http://127.0.0.1:8008](http://127.0.0.1:8008)

Rembember that all our doc files are markdown files. It means you can just dig
around and open them your self.

## How do I contribute?

It's very easy. Just add a markdown file(i.e. foo.md) to a related folder (like
client or backend). After adding the file modify the related index file
(i.e. backend/index.md) and add a new line with the new file name:

    * [new foo document](/backend/foo.md)

Or just examine the wiki folder. You'll see that it has an simple structue.

## Why do we change the index.md everytime we add a new file?

Because in the future there will be lots of files. It's very easy to miss or
lost in those files. This is common problem amongst all wiki platforms. 

Thus the easiest way to handle is to just add a simple line to the related
sections **index.md** file. Markdoc is can generate an automatic list of all files,
however its ugly and doesn't provide much info. The best way is to a maintain
seperate index (home) files for each section.

## I have more questions...

Sent an email to **fatih at koding dot com**
