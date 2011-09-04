Install
---------------------------------------

First install ruby and rubygem (if there are not installed on your system) then:

        gem install genit

All other dependencies will be downloaded and installed automatically.


Create Your Project
---------------------------------------

On the command line, type:

        genit create -e my-site
        cd my-site

### Edit The Home Page

All pages go to the `my-site/pages/` folder. Open the `my-site/pages/index.html` in your favorite editor
and modify its content as follow:

        <h1>Welcome to Genit !</h1>
        <p>This is my first Genit site.</p>
        <div id="footer">
            <p>copyrighted by me</p>
        </div>

### Add A New Page

Create a new file in the `my-site/pages/` folder and name it `about.html`.
Copy/paste the following code in that file:

        <h1>The About Page</h1>
        <p>This is a page about me.</p>
        <div id="footer">
          <p>copyrighted by me</p>
        </div>
    
### Edit The Menu Template

In the `my-site/templates/` folder there is a `menu.html` file. Open it in your editor.
Edit this file as follow:

        <ul id="menu">
          <li><a href="index.html">home</a></li>
          <li><a href="about.html">about</a></li>
        </ul>

Compile your project
----------------------------------------------------

Now you have to 'compile' your site before seeing the result.

        genit compile

There is a shortcut for this command:

        genit cc

Then go to the `my-site/www/` folder and open the `index.html` with your browser.
Congratulations ! You have made your first project using genit.


Refactor your project
--------------------------------------------------

The two pages (index.html and about.html) have the same structure. Especially the footer
section are identical. Let's refactor that.

Create a file named `footer.html` in the `my-site/fragments/` folder and copy paste this code into it:

        <div id="footer">
          <p>copyrighted by me</p>
        </div>

Now edit the `my-site/pages/index.html` as follow:

        <h1>Welcome to Genit !</h1>
        <p>This is my first Genit site.</p>
        <genit class="fragment" file="footer.html"/>

Do the same thing with the page `my-site/pages/about.html`:

        <h1>The About Page</h1>
        <p>This is a page about me.</p>
        <genit class="fragment" file="footer.html"/>

Now, recompile your site with:

        genit cc

then open the `my-site/www/index.html` with your browser.

Ok, as the footer will appear in all our pages, we should put it in the template. 
To do so, remove the footer from the pages:

In `my-site/pages/index.html`:

        <h1>Welcome to Genit !</h1>
        <p>This is my first Genit site.</p>

In `my-site/pages/about.html`:

        <h1>The About Page</h1>
        <p>This is a page about me.</p>

And now add it to the template. The template is in the `my-site/templates/` folder, under the
name `main.html`.

In `my-site/templates/main.html`:

        <?xml version="1.0" encoding="UTF-8"?>
        <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
            "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
        <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
            <head>
                <title>Genit - Static web site framework</title>
                <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
                <link rel="stylesheet" type="text/css" media="all" href="styles/alsa/all.css" /> 
                <link rel="stylesheet" type="text/css" media="screen" href="styles/screen.css" /> 
                <link rel="stylesheet" type="text/css" media="print" href="styles/print.css" /> 
            </head>
            <body>
                <genit class="menu" />
                <genit class="pages" />
                <genit class="fragment" file="footer.html"/>
            </body>
        </html>


Using Markdown
-------------------------------------------------

If a part of a page doesn't need to use html tag attributes (id an class), markdown syntax is
much cleaner than html syntax. Why not using markdown ?

Edit the `my-site/pages/index.html` page as follow:

        <genit class="fragment" file="index_content.markdown"/>
        <genit class="fragment" file="footer.html"/>

Then add this `index_content.markdown` file in the `my-site/fragments/` folder:

        Welcome to Genit !  
        ==================
        
        This is my first Genit site.
        
        I'm using HTML and markdown !

Now recompile your project with `genit cc` before being able to view the change.


Styling your site
--------------------------------------------------------------

Edit the `my-site/styles/screen.css` file as follow:

        a#selected { color:red; }

Recompile your project with:

        genit compile
    
or its shortcut:

        genit cc

and reopen the index.html with your browser to see what's changed.

