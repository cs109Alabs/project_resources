# CS109A Sample Web site


## Setup

1.   Get a copy of this repository in your local GitHub account. This is called _forking_.

    Follow the instructions at [GitHub help for forking](https://help.github.com/articles/fork-a-repo/). Instead of
    `octocat/Spoon-Knife`, use `https://github.com/cs109Alabs/project_resources`

    **Important**: follow only the steps to *Fork a Sample Repository* and
     *Keep your fork synced, Steps 1 and 2*. **Do not do Step 3: Configure Git to sync your fork with the original Spoon-Knife repository**

    We want you to use this repository as a starter template and not sync back
    to it as you make your changes.

2. Publish your copy of the site as a public GitHub page

    * From your copy of the project (`https://github.com/<myuser>/project_resources`),
    click on  `Settings`
    * Change the Project Name to something more friendly like `superawesome`. No spaces
    are allowed. Click on `Rename`.
    * Go back to the Settings page, scroll down to GitHub pages. Set the source to
    `master branch /docs folder` and click on `Save`.
    * Try it! In your browser, go to `https://<myuser>.github.io/superawesome`

    Congratulations! You have published your first web site.


### Exercise 1 - Export an iPython Notebook to HTML and publish it on the web

A copy of a full featured Jupyter notebook was obtained from  [https://github.com/fonnesbeck/multilevel_modeling](https://github.com/fonnesbeck/multilevel_modeling)

A copy of this notebook and related data is in your local copy of the repository.
We are now going to publish it to the web.

If you'd like to examine it before publishing open `multilevel_modeling.ipynb` locally.

1.   Convert the notebook to static HTML. Assuming the setup is complete, there
is a local directory that corresponds to the project on GitHub

    In the terminal window, enter:

    ```
    cd project_resources
    jupyter nbconvert --to html --template full --output docs/page1.html multilevel_modeling.ipynb
    ```

2.   Push the changes to GitHub

  ```
  git add .
  git commit -m "notebook converted"
  git push
  ```

Once that is complete, navigate to `https://<myuser>.github.io/superawesome/page1.html`

You have now converted a Jupyter notebook to a static HTML page.

At this point, there is a choice to make:

* Put your publishable content in the docs subdirectory of this project
* Create a /docs directory of your current git project repository and change the
project settings to publish it.

### Exercise 2 - Link Pages

In this exercise, a second notebook will be linked to the first notebook.

Back in your `project_resources` directory, open `Chapter8.ipynb`. (This
  file is modified from https://github.com/JWarmenhoven/ISLR-python/blob/master/Notebooks/Chapter%208.ipynb)

First at the top, you'll notice that it is easy to embed links to sections
within the same page. This table of contents helps your readers navigate
the content. Examine the third cell:

```
- [8.1.1 Regression Trees](#8.1.1-Regression-Trees)
```

The text inside the `[]` is how the link is displayed. The text
text inside the `()` is the destination of the link.
([More info about links inside pages](http://sebastianraschka.com/Articles/2014_ipython_internal_links.html))

Add a new line to end of this cell:
```
- [Harvard Home Page](http://www.harvard.edu)
```

When you execute this cell and click on the new link, a new window will
open with Harvard's home page.

To avoid opening a new page, explicit HTML has to be used. Create a new cell
and enter:

```
%%html

<a href="http://www.harvard.edu" target="_self">Harvard Home Page</a>
```

Rather than an interpreted Markdown cell, this new cell contains just
HTML. When running it locally, Jupyter will ask if you want to leave
the page. Since we will export this page to static HTML, it will
not be an issue for readers.

Let's change this to a link to the first page:

```
%%html

<a href="page1.html" target="_self">First Project Page</a>
```

This is a *relative* link (no leading `http://`). By default, the browser will
find the page in the same directory. Let's publish this page and test it.

Go back to terminal, create the HTML and push to GitHub:
```
jupyter nbconvert --to html --template full --output docs/page2.html Chapter8.ipynb
git add .
git commit -m "added links between pages"
git push
```

From your browser, navigate to `https://<myuser>.github.io/superawesome/page2.html`
and test the link to page 1.

### Exercise 3 - Customize Notebook

Let's say you don't want your code messing up your nice web page.

Open up the `Chapter8.ipynb` file again.

Add a cell at the top with the following contents:
```
from IPython.display import HTML

HTML('''<script>
code_show=true;
function code_toggle() {
 if (code_show){
 $('div.input').hide();
 } else {
 $('div.input').show();
 }
 code_show = !code_show
}
$( document ).ready(code_toggle);
</script>
<form action="javascript:code_toggle()"><input type="submit" value="Click here to toggle on/off the raw code."></form>''')
```

This will add a button on the top of the page that allows readers to toggle
the code on or off. It is off by default.

(Courtesy of [StackOverflow](http://stackoverflow.com/questions/27934885/how-to-hide-code-from-cells-in-ipython-notebook-visualized-with-nbviewer))

Go back to terminal, create the HTML and push to GitHub:
```
jupyter nbconvert --to html --template full --output docs/page2.html Chapter8.ipynb
git add .
git commit -m "add toggle button for code"
git push
```

Now by default your HTML page will be clean, but still allow drill down into the code.

Questions? Comments? Ask on Piazza.
