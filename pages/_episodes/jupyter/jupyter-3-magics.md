Magics constitute a simple command language that significantly extends the
power of Jupyter notebooks. There are two types of magics:

* **Line magics**: Commands that are prepended by `%`, and whose arguments only
  extend to the end of the line.
* **Cell magics**: Commands that start with `%%` and then apply to the whole
  cell. Must be written on the first line of a cell.

Now list all available magics with `%lsmagic` (which itself is a magic). You
add a question mark to a magic to show the help (*e.g.* `%lsmagic?`). Some of
them act as shortcuts for commonly used shell commands (`%ls`, `%cp`, `%cat`,
..). Others are useful for debugging and optimizing your code (`%timeit`,
`%debug`, `%prun`, ..). For more information see the
[magics documentation](https://ipython.readthedocs.io/en/stable/interactive/magics.html).

A very useful magic, in particular when using shell commands a lot in your
work, is `%%capture`. This will capture the stdout/stderr of any code cell and
store them in a Python object. Run `%%capture?` to display the help and try to
understand how it works. Try it out with either some Python code, other magics
or shell commands. Here is an example of how you can make it work:

```no-highlight
%%capture output
%%bash
echo "Print to stdout"
echo "Print to stderr" >&2
```

... And in another cell:

```python
print("stdout:" + output.stdout)
print("stderr:" + output.stderr)
```

> **Tip** <br>
> You can capture the output of some magics directly like this: `my_dir = %pwd`.

The `%%script` magic is used for specifying a program (Bash, Perl, Ruby, ..)
with which to run the code (similar to a shebang). For some languages it's
possible to use these shortcuts:

* `%%ruby`
* `%%perl`
* `%%bash`
* `%%html`
* `%%latex`
* `%%R`

> **Note on R code** <br>
> In order to use the `%%R` magic you need to install the `rpy2` extension, for
> example with Conda. This package is already installed in the `jupyter-env`
> environment you're using for this tutorial. However, you also have to load it
> by running `%load_ext rpy2.ipython` in a cell.

Try this out if you know any of the languages above. Otherwise you can always
try to print the quadratic formula with LaTeX!

```no-highlight
\begin{array}{*{20}c} {x = \frac{{ - b \pm \sqrt {b^2 - 4ac} }}{{2a}}} & {{\rm{when}}} & {ax^2 + bx + c = 0} \\ \end{array}
```

Another useful magic is `%precision` which sets the floating point precision
in the notebook. As a quick example, add the following to a cell and run it:

```python
float(100/3)
```

Next set the precision to 4 decimal points by running a cell with:

```
%precision 4
```

Now run the cell with `float(100/3)` again to see the difference.

Running `%precision` without additional arguments will restore the default.

> **Quick recap** <br>
> In this section we've learned:
>
> - The basics of Jupyter magics and the difference between line magics and cell
> magics
> - How to capture and use output from notebook cells with `%%capture`
> - How to use magics to run non-Python code in notebooks
