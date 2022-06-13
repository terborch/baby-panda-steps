# baby-panda-steps
First steps into data analysis with Jupyter

# Installing python
The python distribution we will use is Anaconda, available for free for non-commercial use at this link:
https://www.anaconda.com/products/distribution

The advantage of Anaconda is that it comes bundled up with the most popular datascience modules of python like pandas, numpy and many more. Otherwise all of these would need to installed separately.

If your are having trouble installing Anaconda, read the docs ! https://docs.anaconda.com/anaconda/install/

# Launching Jupyter Notebook
Jupyter Notebook is the interface we will use for data analysis. Often referred to as a notebook, it is very easy to use and great to learn python or explore messy data. The best practice for a notebook is trial and error, break and repair. A messy but intuetive way to learn. Just remember to cleen it up before you close it down, lest you will hate your past self!

## Create a folder
Create work folder where you want to store your data and jupyter notebook. A best practice is to avoid spaces (use underscore _ ) and spectial characters like -, . or é in the folder and file names in general. To get started, we can download some sample data in the .csv format form https://www.gapminder.org/data/. I will use the average number of babies per woman in the CSV format.

In your work folder, creat a folder named "data" and add the dara file from gapminder into it. Rename the file "gapminder babies per woman.csv".

## 3, 2, 1... Launch
Launching jupyter is incredibly easy, follow these few steps:
1. copy the link to your work directory. (on Windows, simply select the path in the folder seach bar)
2. search for "anaconda" in the application search bar and start "Anaconda Prompt"
3. in the anaconda comand window tpye `cd "path\to\my\directory"`
4. hit enter, the active path should now be to your python work directory
5. type `jupyter notebook` hit enter, voilà

A browser window opens, don't panic, it's the jupyter notebook interface. It is not online, but it runs in your browser. You should see the contents of your folder.

To create a new jupyter notebook click `new` and `Python 3`. Your can rename your notebook by clicking "Untitled" in the upper left corner.

# Basic coding with pandas

All the questions on how to do anything with pandas is here https://pandas.pydata.org/docs/user_guide/index.html, or a short google search "open excel file pandas" away... It's one of the most used libraries so go ahead and search away, you will never be the first to ask.

## Importing pandas
Pandas is a open source module that is not part of python. Fortunately you have already downloaded and install pandas by installin Anaconda. To start using all the pandas functionallities type:

```python
# import the pandas module and abreviate the module as "pd"
import pandas as pd
```

To execute this command line, hit `shift + enter`. This executes the code block and creates a new code block, or moves to the next one.

A bit more info on what is going on:
* To the left of the command block you see [\*] indicating the code is running. Then [1] indicating the code has executed properly.
* The sentence above the comand line starting with # is a comment explaining in plain english what the code below does. It is super usefuel to type out in plain english, using #, what your code does, or you will hate your lasy past self for not doing it.
* Don't worry if the colours in the text abore is not the same, every editor uses different colour pattens to highlight what is what.

## Opening a data file
Pandas is meant for reading, exploring, transforming and then saving data. Usually in the form of 2D tables. To open a file type:

```python
# define the file_name variable
file_name = "gapminder babies per woman.csv"

# create a path to the data file inside the data folder
import os
file_path = os.path.join("data", file_name)
```

Hit `shift + enter` and type `file_path` in the new cell, and execute that cell. The output should be the full path, with a \\ separator between the folder and file name as is the case on windows.

In a new code block, type the following. Your data is now loaded !

```python
# read the data file into a pandas dataframe nicknamed df and then display its content
df = pd.read_csv(file_path)
df
```

## Selecting a column

```python
# selecting the column titled 2017
df["2017"]
```

## Applying filters
With pandas we can easily filter using conditions on specific columns. For example:

```python
# only keep the rows, where, in the year 2017, the birthrate was higher than or equal to 3
df[df[2017] >= 3.0]
```

The logical operators for python and many languages are:
* `==` exactly equal to
* `!=` not equal to
* `>` greater than
* `<=` smaller or equal to
* etc...

You can even combine multiple filters using `and` or `or`

```python
# only keep the rows, where, in the year 2017, the birthrate was lower than 2 and in the year 1920, the birthrate was higher than 4
df[(df[2017] < 2.0) and (df[1920] > 4.0 )]
```

Note that this only displays the filtered data, but the df dataframe is unchanged. To save changes we would need to write:

```python
df = df[(df[2017] < 2.0) and (df[1920] > 4.0 )]
```

## Saving data in an Excel file
```python
# save the filtered dataframe as an excel file named "filtered data"
df.to_excel("filtered data.xlsx")
```

# Some tips for jupyter notebook
* Erase a code block: select the block by clicking to the right of it, in the empty space and press the "x" key
* Restart the otebook: klick "kernel" and select "restart and run all". This should be done regulaly. It should be the first thing to do whenever an error appears to make sure that the error is not caused by simply not executing each code block in the right order.

# Going further
An excellent video series on pandas (and many other topics) https://www.youtube.com/watch?v=ZyhVh-qRZPA&list=PL-osiE80TeTsWmV9i9c58mdDCSskIFdDS

Android application sololearn offers a free hands on intorduction to phython which helped me alot https://www.sololearn.com/home 

# Disclaimer
This example code has not been tested and this text has not been proof read, typos may cause errors !
