# Coding Guide

This is a lose collection of soft and hard guidelines for your project.
You will find some information, on what coding patters I prefer and what you should pay attention to.
You will also find a example of how the folder structure for your project should look like.

You do not adhere to my suggestions, if you have a prefered alternative. But you have to make a decision
and be consistent. 


## Formatting
- Use Type Hinting in Python (this is mandatory)
- I recommend using snakecase for varibale naming: `variable_a` or `accuracy_training`
- Use a code formatter, I recommend default [black](https://github.com/psf/black)
- use github and commit regulary

[Here](https://khuyentran1401.github.io/Efficient_Python_tricks_and_tools_for_data_scientists/Chapter1/good_practices.html) 
is some more information on more general good python practices.

## Figures

Here are some basic tips for making figures in Python.

- Use `seaborn` and use `matplotlib` only as support.
- Always export all figures as `.png`, `.svg` and `.pdf`. This way you can make small changes
 without having to generate the plot again
- Always export images with 300dpi, `dpi = 300`
- Always use `transparent = True` when exporting
- Always use `seaborn.despine()` before exporting

Example:
```python
import seaborn as sns
from matplotlib import pyplot as plt

x = [1,2,2,3,3,3,4,4,5]
sns.kdeplot(x, fill = True)
plt.xlabel("Random Values")
sns.despine()
plt.save_figure("path_to_file.png", transparent = True, format = "png", dpi = 300)

``` 
## Example Project

This is the folder structure of an example project. It is by no means complete and you can always add subfolder yourself.
You do not have to use it, if you have a system that works for you. But if you do not I recommend you start with this one.

### data
The data that is used within this project, goes into the `data` folder. You can have subfolders seperating cleaned and
uncleaned data. 

### src

here are all your scripts, the main scripts should be directly located in `src/`. Any utility functions that are imported
should be placed in the utils folder from which you import them. You can add further subfolder to utils if needed.

### results

Here all your results should be saved. Seperated them into `figures`, `tables` and `raw`.
In `raw` you can save `.csv` files, that not have yet been prepared in any presentable form.
`figures` contains all your figures. I recommend always exporting in at least **300 dpi** and a transparent backgroud `transparent=True`.
Further, you should always save every figure in `svg`, `png` and `pdf` format. This allows you to make quick changes
to the figure (like colors) wihthout having to re-run the code.

### environment.yml

Every final project should be accompanied by a **clean** enviornment.yml that contains the packages needed to run your code.
You can use `conda` to generate such file. However, this is a very messy file, and very restrictiv. So you need to manually 
clean the file and only keep the libraries that would have to be activily be installed by the user.

### README.md

This file should contain all information how to run your experiments.

### .gitignore
contains all files and folders that should not be commited to the repo
  

