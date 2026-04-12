# homework-0-masonxmh

Mason(Mohan) Xing
USCID:	6880083372

#### Pandas

This section is for practicing basic funtions of the Pandas library using the Salaries
data set.
(a) Consider the Salaries.csv file.
(b) Use the read_csv(...) method from Pandas (Documentation Link) to read data
from file Salaries.csv and to copy it into a dataframe.
(c) Make the column playerID in the csv file as the index column and the first row
as the header. Also, skip the second row when reading the file.
(d) Select the id of the players who are registered in ATL and HOU whose salary is
higher than one million.
(e) Use the describe() method to calculate the standard deviation, first quartile, median,
third quartile, mean, maximum, and minimum of the salary in team ATL.
(f) Create a Python dictionary object whose keys are the headers of the dataframe
created in the read_csv() exercise and values are Python list objects that contain
data corresponding to the headers. (Here, use the iterrows() method to iterate
each row of the dataframe and copy it to a dictionary. However, there is an easier
way. Learn how the to_dict() method works by yourself later)
(g) Create a dataframe using pd.DataFrameRead (Documentation Link) and from
the dictionary created in (e). Then, change the header to "a", "b", "c", ... .

#### Numpy
(a) Create a 2-dimensional Python list object, then convert it to a Numpy array
object.
(b) Examine the ndim, shape, size, dtype, itemsize, and data attributes of the numpy
array object. Make sure you understand their functions.
(c) Learn the dimension concept of an ndarray object by using reshape() and flatten()
methods.
(d) Understand how the slice operation works for 1-D arrays and 2-D arrays and
practice by yourself.
(e) Learn operations on ndarray by examining the argmin(), argmax(), min(), max(),
mean(), sum(), std(), dot(), square(), sqrt(), abs(). exp(), sign(), and mod()
methods. Make yourself comfortable with these methods.
(f) Examine the arange(), ones(), zeros(), eye(), linspace(), and concatenate() methods.
Make yourself comfortable with these methods.

#### Matplotlib
(a) Create two one dimensional arrays x and y and plot y vs x, add title, xlabel,
ylabel, grid.
(b) Create multiple arrays and plot them with different styles, add legends, add
text/mathematical equations on the plot.
(c) Create multiple subplots, play around with the figure size, text font/size.
(d) Get familiar with get current axis (gca) handle to do the above tasks
(e) Change the limits on x and y axes, use logarithmic axes to plot.

#### Seaborn
(a) Use the Salaries.csv file in Pandas section.
(b) Create a dataframe and try to plot it with seaborn.
(c) Perform statistical estimation on the data using seaborn in-built functions - lmplot,
catplot, relpolt.
(d) Create axis level functions like boxplot to visualize
(e) Visualize the dataset structure using pairplot and jointplot.