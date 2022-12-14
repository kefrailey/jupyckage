# README

*A tiny little package to create packages from jupyter notebooks*

If you find yourself copy pasting functions between jupyter notebooks, this might help.

Please note: this allows you to import functions *and* objects from your notebooks.


### Typical Use Cases
This is very helpful when producing the same graph, running the same ETL, or executing the same ML pipeline on different datasets or different versions of the same dataset.

## Make Packages from Jupyter Notebooks

### In Python

You can run this **in** <your_notebook.ipynb> or anywhere else in the same directory

```
from jupyckage.jupyckage import notebook_to_package

notebook_to_package("notebook_name.ipynb")
```

will create the needed files and directories [in the current directory] to produce a local package 
#### Importing the Package

You can access by 
```
import notebooks.src.<cleaned_notebook_name>.<cleaned_notebook_name>
```

where `cleaned_notebook_name` is all lower case and has spaces replaced with underscores. *Please note* if your notebook name has illegal characters for a python package, there will be an error.


I recommend importing your notebook `as` an abbreviation-- but as usual **please do not import \***, for the same reasons as usual.

**Make sure to rerun the code if you want the package updated.**

### From the Command Line

You can enter 

```
jupyckage --nb <notebook_name.ipynb>
```
 
in your terminal and the most recent *saved* version of your notebook will be turned into a package.  You can import the package as described above in 'In Python'



### Under the Hood: Package Directory Structure

With no consensus on directory structure for packages, I defaulted to a version of [python.org's suggestion](https://packaging.python.org/en/latest/tutorials/packaging-projects/#creating-the-package-files).

    notebooks/
    ├── src/
    │   └── <notebook_name>/
    │       ├── __init__.py
    │       └── <notebook_name>.py  # what you'll be importing
    └── bin/
        └── <notebook_name>.py #executable

I realize the import statement is hefty, but I didn't want to handle collissions in a VO.


## Skip Stuff

Aything you don't want included in the package you can put below a MARKDOWN cell including the text between the quotes

```
"# DO NOT ADD BELOW TO SCRIPT"
```

## FAQs

### Help! My code isn't updating!

Make sure that you've run your notebook and saved it.  This package relies on jupyter notebook's `nbconvert` under the hood, which looks to the most recent checkpoint of your notebook.

### Help! Why can't jupyckage do more?!?!

If you're interested added functionality, please let me know and I'll look at adding it or happily work with you so you can contribute :) 

### Help! Why is the import statement so verbose?!?!

I realize the import statement is hefty, but I didn't want to handle collissions in a VO.  If you find this package useful and would really love an update or want to contribute, please contact me :) 


## Contact
Hi, I'm Kerstin Frailey.  I whipped up this package quickly to make my life a bit easier.  Hope it helps some other people out, too.

Here's the repo info:

+ code https://github.com/kefrailey/jupyckage
+ issues https://github.com/kefrailey/jupyckage/issues

Here's my contact info:

+ twitter @KEFrailey
+ blog datascienceatwork.blog
+ email frailey.work@gmail.com
+ linkedin linkedin.com/in/kefrailey

Hope you have a nice day!