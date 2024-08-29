One thing that sets Jupyter Notebook apart from what you might be used to is
that it's a web application, *i.e.* you edit and run your code from your
browser. But first you have to start the Jupyter Notebook server. At this
point you may either try the classic notebook interface by running:

```bash
jupyter notebook --allow-root
```

Or give the more feature-rich Jupyter lab interface a try by running:

```bash
jupyter lab --allow-root
```

Whichever interface you choose you should see something similar to this
printed to your terminal:

```no-highlight
[I 18:02:26.722 NotebookApp] Serving notebooks from local directory: /Users/john/workshop-reproducible-research/tutorials/jupyter
[I 18:02:26.723 NotebookApp] 0 active kernels
[I 18:02:26.723 NotebookApp] The Jupyter Notebook is running at:
[I 18:02:26.723 NotebookApp] http://localhost:8888/?token=e03f10ccb40efc3c6154358593c410a139b76acf2cae000
[I 18:02:26.723 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 18:02:26.724 NotebookApp]

    Copy/paste this URL into your browser when you connect for the first time,
    to login with a token:
        http://localhost:8888/?token=e03f10ccb40efc3c6154358593c410a139b76acf2cae785c
[I 18:02:27.209 NotebookApp] Accepting one-time-token-authenticated connection from ::1
```

> **A note for Windows users** <br>
> If you see the error message `Start : This command cannot be run due to the
> error: The system cannot find the file specified. ...` then try starting
> Jupyter with `jupyter notebook --no-browser` then copy the URL given into the
> browser directly.


> **Jupyter notebook versions** <br>
> Depending on what version of the `notebook` conda package you have installed,
> the interface may look slightly different. The screenshots in this tutorial
> are from version 7, an update which has brought the 'classic' Jupyter notebook
> closer to the Jupyter lab interface. Read more about this update at the
> [Jupyter homepage](https://jupyter-notebook.readthedocs.io/en/latest/migrate_to_notebook7.html).

The Jupyter Notebook/Lab interface probably opened up a web browser for you
automatically, otherwise go to the address specified in the message in the
terminal. Note that the server is running locally (as
`http://localhost:8888`) so this does not require that you have an active
internet connection. Also note that it says:

```no-highlight
Serving notebooks from local directory: </some/local/path/workshop-reproducible-research/tutorials/jupyter>
```

Everything you do in your Notebook session will be stored in this directory, so
you won't lose any work if you shut down the server.

> ![](images/jupyter_dashboard.png){ width=700px }

What you're looking at is the Notebook dashboard. This is where you manage your
files, notebooks, and kernels. The Files tab shows the files in your directory.
The Running tab keeps track of all your processes.

The Jupyter lab dashboard should look something like this:

> ![](images/jupyterlab_dashboard.png){ width=700px }

Let's start by creating an empty notebook. You can do this by selecting the
Files tab and clicking New > Notebook. When the notebook opens, select the
suggested Python 3 kernel from the drop-down menu.

This will open up a new tab or window looking like this:

> ![](images/jupyter_empty_nb.png){ width=700px }

Start by giving your notebook a name by clicking on the text "Untitled" at the
top of the page. Enter "jupyter-tutorial.ipynb".

Note that for most of this tutorial we will describe how you work in the actual
notebook and not devote a lot of time to the extra features available in the
Jupyter lab interface.

> **Tip** <br>
> If you want to start Jupyter Notebooks on a cluster that you SSH to (_e.g._
> Uppmax) see the section in the
> [Extra material](jupyter-10-extra-material)

Jupyter notebooks are made up of cells, and you are currently standing in
the first cell in your notebook. Your cursor should be blinking in this cell,
indicating that you are in "Edit mode" meaning that you can type text in the
cell. Pressing the `Esc` key puts you in "Command mode" which allows you to
manipulate the notebook as a whole, more on this later.

Cells in Jupyter notebooks can be of two types:*markdown* or *code*.

* **Markdown:** 

These cells contain static material such as captions, text, lists, images and so
on. You express this using Markdown, which is a lightweight markup language.
Markdown documents can then be converted to other formats for viewing (the
document you're reading now is written in Markdown and then converted to HTML).
The format is discussed a little more in detail in the [Quarto
tutoriall](quarto-1-introduction). Jupyter Notebook uses a dialect of Markdown
called GitHub Flavoured Markdown, which is described
[here](https://guides.github.com/features/mastering-markdown/).

* **Code:** 

These are the cells that actually do something, just as code chunks do in
Quarto/R Markdown. You can write code in dozens of languages and do all
kinds of clever tricks. You then run the code cell and any output the code
generates, such as text or figures, will be displayed beneath the cell. We
will get back to this in much more detail, but for now it's enough to
understand that code cells are for executing code that is interpreted by a
kernel (in this case the Python version in your Conda environment).

Before we continue, here are some shortcuts that can be useful. Note that they
are only applicable when in "Command mode". Most of them are also available from
the menus. You can also view this list of shortcuts from the **Help** menu under
"Show Keyboard Shortcuts".

<table class="table table-hover table-condensed" border=1; style="width:400px; margin-left:auto; margin-right:auto;">
    <thead style="background-color:#DAE7F1">
        <tr>
            <td style="padding:5px; text-align:center;"> <font size="3"><b> Shortcut </b></td>
            <td style="padding:5px"> <font size="3"><b> Effect </b></td>
        </tr>
    </thead>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `enter` </td>
        <td style="padding:5px"> <font size="3"> enter Edit mode </td>
    </tr>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `escape` </td>
        <td style="padding:5px"> <font size="3"> Enter Command mode </td>
    </tr>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `ctrl` - `enter`</td>
        <td style="padding:5px"> <font size="3"> Run the cell </td>
    </tr>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `shift` - `enter`</td>
        <td style="padding:5px"> <font size="3"> Run the cell and select the cell below </td>
    </tr>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `alt` - `enter`</td>
        <td style="padding:5px"> <font size="3"> Run the cell and insert a new cell below </td>
    </tr>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `s`</td>
        <td style="padding:5px"> <font size="3"> Save the notebook </td>
    </tr>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `tab` </td>
        <td style="padding:5px"> <font size="3"> For code completion or indentation </td>
    </tr>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `m`, `y`</td>
        <td style="padding:5px"> <font size="3"> Toggle between Markdown and Code cells </td>
    </tr>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `d`- `d` </td>
        <td style="padding:5px"> <font size="3"> Delete a cell </td>
    </tr>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `a` </td>
        <td style="padding:5px"> <font size="3"> Insert cells above current cell </td>
    </tr>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `b` </td>
        <td style="padding:5px"> <font size="3"> Insert cells below current cell </td>
    </tr>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `x` </td>
        <td style="padding:5px"> <font size="3"> Cut currently selected cells </td>
    </tr>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `v` </td>
        <td style="padding:5px"> <font size="3"> Paste cell below </td>
    </tr>
    <tr>
        <td style="padding:5px; text-align:center;"> <font size="3"> `o` </td>
        <td style="padding:5px"> <font size="3"> Toggle output of current cell </td>
    </tr>
</table>


## Writing markdown

Let's use our first cell to create a header. Change the format from Code to
Markdown using the drop-down list in the Notebook Toolbar, or by pressing the
`m` key when in command mode. Double click on the cell, or hit `enter` to enter
editing mode and input "# My notebook" ("#" is used in Markdown for header 1).
Run the cell with `ctrl`-`enter` (`cmd`-`enter` on Mac).

Markdown is a simple way to structure your notebook into sections with
descriptive notes, lists, links, images etc.

Below are some examples of what you can do in markdown. Paste all or parts
of it into one or more cells in your notebook to see how it renders. Make
sure you set the cell type to Markdown.

```
## Introduction
In this notebook I will try out some of the **fantastic** concepts of Jupyter
Notebooks.

## Markdown basics
Examples of text attributes are:

* *italics*
* **bold**
* `monospace`

Sections can be separated by horizontal lines.

---

Blockquotes can be added, for instance to insert a Monty Python quote:

> Spam!
> Spam!
> Spam!
> Spam!

See [here](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Working%20With%20Markdown%20Cells.html) for more information.
```

## Writing code

Now let's write some code! Since we chose a Python kernel, Python would be the
native language to run in a cell. Enter this code in the second cell and run
it:

```python
print("Hello world!")
```

Note how the output is directly displayed below the cell. This interactive way
of working is one of the things that sets Jupyter Notebook apart from RStudio
and Quarto. In RStudio/Quarto, documents are typically rendered top-to-bottom in one run, while
you work *in* a Jupyter notebook in a different way. This requires some special
attention when it comes to reproducibility, which we will get back to in the
[reproducibility](jupyter-7-reproducibility) section.

What **is** a Jupyter notebook? Let's look a closer at the notebook we're
currently working in. Jupyter Notebooks are autosaved every minute or so, so you
will already have it available. We can be a little meta and do this from within
the notebook itself, by running some shell commands in a code cell. This very
handy functionality is possible by prepending the command with `!`. Try adding
`!ls` to a code cell and run it. This will list the files in the current directory.

Aha, we have a new file called `jupyter-tutorial.ipynb`! This is our notebook. Look at
the first ten lines of the file by using `!head jupyter-tutorial.ipynb`. Seems like it's
just a plain old JSON file. Since it's a text file it's suitable for version
control with for example Git. There are however some special considerations to
take into account for Notebooks which we will cover in the [reproducibility
section](jupyter-7-reproducibility) of this tutorial.

Variables defined in cells become variables in the global namespace. You can
therefore share information between cells. Try to define a function or variable
in one cell and use it in the next. For example, add the following to a new cell
and run it:

```python
def print_me(str):
    print(str)
```

Now create a new cell and add:

```python
print_me("Hi!")
```

Your notebook should now look something like this.

> ![](images/jupyter_basic_update.png){ width=700px }

The focus of this tutorial is not on how to write Markdown or Python; you can
make really pretty notebooks with Markdown and you can code whatever you want
with Python. Rather, we will focus on the Jupyter Notebook features that allow
you to do a little more than that.

> **Quick recap** <br>
> In this section we've learned:
>
> - That a Jupyter notebook consists of a series of cells, and that they can
>   be either markdown or code cells.
> - That we execute the code in a code cell with the kernel that we chose
>   when opening the notebook.
> - We can run shell commands by prepending them with `!`.
> - A Jupyter notebook is simply a text file in JSON format.
