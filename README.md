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
    are allowed.
    * Continuing on the Settings page, scroll down to GitHub pages. Set the source to
    `master branch /docs folder` and save it.
    * Try it! In your browser, go to `https://<myuser>.github.io/superawesome`

    Congratulations! You have published your first web site.


### Exercise 1 - Export an iPython Notebook to HTML and publish it on the web

A copy of a full featured Jupyter notebook was obtained from  [https://github.com/fonnesbeck/multilevel_modeling](https://github.com/fonnesbeck/multilevel_modeling)

A copy of this notebook and related data is in your local copy of the repository.
We are now going to publish it to the web.

If you'd like to examine it before publishing open `multilevel_modeling.ipynb` locally.

To publish it to the web, from the terminal window, enter:

```
jupyter nbconvert --to html --template full --output docs/page1.html multilevel_modeling.ipynb
```

Once that is complete, navigate to `https://<myuser>.github.io/superawesome/page1.html`



### Exercise 2 - Update the CSS to change the style

[Start Exercise 2](exercise2.md)



## Reference Commands

### Switching to the `gh-pages` branch

From the terminal window, go to the directory that contains this project

```
cd project_resources
git checkout gh-pages
```

### Switching back to the `master` branch

From the terminal window, go to the directory that contains this project

```
git checkout master
```
