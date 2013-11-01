Note
==========

* These notes contain translations from R into Pandas/Numpy/Scipy.
* Notes are based upon Paul Teetor's R Cookbook published by
  O'Reilly
* http://shop.oreilly.com/product/9780596809164.do

Assumptions
===========

The following imports are assumed, as well as the use of ipython as your
python interpreter::

    import pandas as pd
    import numpy as np
    import matplotlib.pyplot as plt

The combination of numpy, pandas, and matplotlib are python's answer to R.
Pandas is built on top of the numpy libraries, which is the basis for a large
amount of scientific computing today.

References below to python really mean python along with pandas, numpy, as
well as matplotlib if any graphing is needed.

A quote from 'Pandas For Data Analysis' by Wes McKinney:


`For users of the R language for statistical computing, the DataFrame name will
be familiar, as the object was named after the similar R data.frame object.
They are not the same, however; the functionality provided by data.frame in R
is essentially a strict subset of that provided by the pandas DataFrame.`


1 - Getting Started and Getting Help
======================================================================

1.1 - XXX
----------------------------------------------------------------------

1.2 - XXX
----------------------------------------------------------------------

1.3 - XXX
----------------------------------------------------------------------

1.4 - XXX
----------------------------------------------------------------------

1.5 - XXX
----------------------------------------------------------------------

1.6 - XXX
----------------------------------------------------------------------

1.7 - XXX
----------------------------------------------------------------------

1.8 - XXX
----------------------------------------------------------------------

1.9 - XXX
----------------------------------------------------------------------

1.10 - XXX
----------------------------------------------------------------------

1.11 - XXX
----------------------------------------------------------------------

1.12 - XXX
----------------------------------------------------------------------

1.13 - XXX
----------------------------------------------------------------------

2 - Some Basics
======================================================================

2.1 - Printing Something
----------------------------------------------------------------------

R::

    # r code here

Python::

    # python code here.

2.2 - Setting Variables
----------------------------------------------------------------------

R::

    x <- 3
    print(x)

Python::

    x = 3
    print(x)

2.3 - Listing Variables
----------------------------------------------------------------------

R::

    # r code here

Python::

    # python code here.

2.4 - Deleting Variables
----------------------------------------------------------------------

R::

    rm(x)

Python::

    del(x)

2.5 - Creating a Vector
----------------------------------------------------------------------

R::

    x <- c(1, 2, 3, 4, 4, 5)

Python::

    x = [1, 2, 3, 4, 4, 5]

Numpy::

    x = np.array([1, 2, 3, 4, 4, 5])

Pandas::

    x = pd.Series([1, 2, 3, 4, 4, 5])
    

2.6 - Computing Basic Statistics
----------------------------------------------------------------------

R::

    x <- c(0,1,1,2,3,5,8,13,21,34)
    y <- log(x+1)

    mean(x)
    median(x)
    sd(x)
    var(x)
    cor(x, y)
    cov(x, y)

    # na.rm=TRUE argument to skip NA values.

    mean(dataframe)
    sd(dataframe)

Python::

    x = np.array([0, 1, 1, 2, 3, 5, 8, 13, 21, 34])
    y = np.log(x + 1)

    np.mean(x)
    x.mean()

    np.median(x)

    # R divides by (N - 1), numpy default to N, ddof changes this.
    x.std(ddof=1)
    np.std(x, ddof=1)

    x.var(ddof=1)
    np.std(x, ddof=1)

    # numpy gives matrix, R just gives coefficients.
    np.cov(x, y)
    np.corrcoef(x, y)

    dataframe.mean()
    dataframe.std(ddof=1)
    

2.7 - Creating Sequences
----------------------------------------------------------------------

R::

    # [1, 5]
    1:5
    # 1, 3, 5
    seq(from=1, to=5, by=2)
    # 1, 1, 1, 1, 1
    rep(1, times=5)

Python::

    # [1, 5] or [1, 6)
    np.arange(1, 6, step=2)
    range(1, 6)    # python iterator (doesn't create entire list, iterator)
    xrange(1, 6)    # python iterator (doesn't create entire list, iterator)

    # 1, 3, 5
    np.arange(1, 6, step=2)

    # 1, 1, 1, 1
    np.ones(4)

    # 3, 3, 3, 3
    x = np.empty(4)
    x.fill(3)


2.8 - Comparing Vectors
----------------------------------------------------------------------

R::

    ==
    !=
    <
    >
    <=
    >=

    any(x == 3)
    all(x == 3)

Python::

    # Basically identical.
    Same logical operators here.
    np.any()
    np.all()

    

2.9 - Selecting Vector Elements
----------------------------------------------------------------------

R::

    # 3rd element.
    v[3]

    # 1st, 2nd, 3rd
    v[1:3]

    # 1, 3, 5.
    v[c(1, 3, 5)]

    v[v < 10]

    v[v > median(v)]

    v[v > np.median(v) | v == 5]

    years <- c(1960, 1964, 1976, 1994)
    names(years) <- c("Kennedy", "Johnson", "Carter", "Clinton")
    years['Carter'] # 1976

Python::

    # 3rd element. Python is zero-indexed, R starts at 1.
    # e.g. first element in R is v[1], in python is v[0]
    v[2]
    v[3 - 1]

    # 1st, 2nd, 3rd
    v[0:3]

    # 1, 3, 5.
    v[[0, 2, 4]]
    np.take(v, [0, 2, 4])

    # Same in R & Python.
    v[v < 10]

    v[v > np.median(v)]

    v[(v > np.median(v)) | (v == 5)]

    years = [1960, 1964, 1976, 1994]
    names = ['Kennedy', 'Johnson', 'Carter', 'Clinton']
    presidents = pd.Series(data=years, index=names)
    # OR
    presidents = pd.Series(data, index)
    
    presidents['Carter']

2.10 - Performing Vector Arithmetic
----------------------------------------------------------------------

R::

    v <- c(4, 2, 3, 5, 4)
    w <- c(5, 2, 3, 4, 5)
    v + w
    v - w
    v * w
    v / w
    w ^ v
    w + 2
    w - 2
    w * 2
    w ^ 2
    w / 2
    2 ^ w

    sqrt(w)
    log(w)
    sin(w)


Python::

    # Basically identical.

    v = np.array([4, 2, 3, 5, 4])
    w = np.array([5, 2, 3, 4, 5])
    v + w
    v - w
    v * w
    v / w
    w ^ v
    w + 2
    w - 2
    w * 2
    w ^ 2
    w / 2
    2 ^ w

    np.sqrt(w)
    np.log(w)
    np.sin(w)

2.11 - Getting Operator Precedence Right
----------------------------------------------------------------------

R::

    # r code here

Python::

    # python code here.

2.12 - Defining a Function
----------------------------------------------------------------------

R::

    cv <- function(x) sd(x) / mean(x)
    # OR
    cv <- function(x) {
        sd(x) / mean(x)
    }

    cv(1:10) # .55048

Python::

    def cv(x):
        return np.std(x, ddof=1) / np.mean(x)

    cv(arange(1, 11)) # .55048



2.13 - Typing Less and Accomplishing More
----------------------------------------------------------------------

R::

    # r code here

Python::

    # python code here.

2.14 - Avoiding Some Common Mistakes
----------------------------------------------------------------------

R::

    # r code here

Python::

    # python code here.

3 - Navigating the Software
======================================================================

3.1 - Getting and Setting the Working Directory
----------------------------------------------------------------------

R::

    # r code here

Python::

    # python code here.

3.2 - Saving Your Workspace
----------------------------------------------------------------------

R::

    # r code here

Python::

    # python code here.

3.3 - Viewing Your Command History
----------------------------------------------------------------------

R::

    history()

Python::
    
    %history

3.4 - Saving the Result of the Previous Command
----------------------------------------------------------------------

R::

    .Last.value

Python::

    _

3.5 - Displaying the Search Path
----------------------------------------------------------------------

R::

    # r code here

Python::

    # python code here.

3.6 - Accessing the Functions in a Package
----------------------------------------------------------------------

R::

    library(packagename)
    some_func()

Python::

    import packagename
    packagename.some_func()
    # OR
    from packagename import some_func
    some_func()

3.7 - Accessing Built-in Datasets
----------------------------------------------------------------------

R::

    #

Python::

    #

3.8 - Viewing the List of Installed Packages
----------------------------------------------------------------------

R::

    #

Python::

    #

3.9 - Installing Packages from CRAN
----------------------------------------------------------------------

R::

    #

Python::

    #

3.10 - Setting a Default CRAN Mirror
----------------------------------------------------------------------

R::

    #

Python::

    #

3.11 - Suppressing the Startup Message
----------------------------------------------------------------------

R::

    #

Python::

    #

3.12 - Running a Script
----------------------------------------------------------------------

R::

    source('somefilename.R')

Python::

    %run somefilename.py

3.13 - Running a Batch Script
----------------------------------------------------------------------

R::

    Rscript somefilename.R

Python::

    ipython -- somefilename.py
    # OR
    python somefilename.py

3.14 - Getting and Setting Environment Variables
----------------------------------------------------------------------

R::

    #

Python::

    #

3.15 - Locating the R Home Directory
----------------------------------------------------------------------

R::

    #

Python::

    #

3.16 - Customizing R
----------------------------------------------------------------------

R::

    #

Python::

    #

4 - Input and Output
======================================================================

4.1 - Entering Data from the Keyboard
----------------------------------------------------------------------

R::

    #

Python::

    #

4.2 - Printing Fewer Digits (or More Digits)
----------------------------------------------------------------------

R::

    # digits defaults to 7.
    print(pi)
    print(pi, digits=2)

    # discouraged by the author.
    # this changes it everywhere.
    options(digits=5)

Python::

    #

4.3 - Redirecting Output to a File
----------------------------------------------------------------------

R::

    #

Python::

    #

4.4 - Listing Files
----------------------------------------------------------------------

R::

    list.files()

Python::

    !ls

4.5 - Dealing with "Cannot Open File" in Windows
----------------------------------------------------------------------

R::

    #

Python::

    #

4.6 - Reading Fixed-Width Records
----------------------------------------------------------------------

R::

    records <- read.fwf('my-data-file.txt', widths=c(10, 10, 4, -1, 4),
                        col.names=c('Last', 'First', 'Born', 'Died'))

Python::

    # widths if contiguous, else use colspecs.
    # colspecs, half open intervals.
    records = pd.read_fwf('my-data-file.txt',
                          colspecs=[((0, 10), (10, 20), (20, 24), (25, 29)],
                          names=['Last', 'First', 'Born', 'Died'])

    # if no space between 'Born' & 'Died'
    records = pd.read_fwf('my-data-file.txt',
                          widths=[10, 10, 4, 4],
                          names=['Last', 'First', 'Born', 'Died'])

4.7 - Reading Tabular Data Files.
----------------------------------------------------------------------

R::

    # default is white-space separator.
    records <- read.table('my-filename.txt')

    # ':' separated.
    records <- read.table('my-filename.txt', sep=':')

    # With column headings.
    records <- read.table('my-filename.txt', header=TRUE)

Python::

    # default is '\t'
    records = pd.read_table('my-filename.txt', header=None)

    # ':' separated.
    records = pd.read_table('my-filename.txt', sep=':', header=None)

    # With column headings.
    records = pd.read_table('my-filename.txt', sep=':')

4.8 - Reading from a CSV Files
----------------------------------------------------------------------

R::

    # default's to reading in headings.
    records <- read.csv('myfile.csv')

    records <- read.csv('myfile.csv', header=FALSE)

Python::

    records = pd.read_csv('myfile.csv')

    records = pd.read_csv('myfile.csv', header=None)

4.9 - Writing to CSV Files.
----------------------------------------------------------------------

R::

    # data in variable 'df'
    write.csv(df, file='some-file.csv', row.names=FALSE)

Python::

    df.to_csv('some-file.csv', index=False)

4.10 - Reading Tabular or CSV Data from the Web
----------------------------------------------------------------------

R::

    df <- read.csv('http://www.justinmrao.com/salary_data.csv')

Python::

    df = pd.read_csv('http://www.justinmrao.com/salary_data.csv'

4.11 - Reading Data from HTML Tables
----------------------------------------------------------------------

R::

    #

Python::

    #

.. TODO
4.12 - Reading Files with a Complex Structure
----------------------------------------------------------------------

R::

    #

Python::

    #

4.13 - Reading from MySQL Databases.
----------------------------------------------------------------------

R::

    library(RMySQL)
    con <- dbConnect(MySQL(),
                     user="userid",
                     password="pswd",
                     host="hostname",
                     client.flag=CLIENT_MULTI_RESULTS)
    sql <- 'SELECT * FROM someTable WHERE City = "Melbourne"'
    df <- dbGetQuery(con, sql)


Python::

    import MySQLdb
    con = MySQLdb.connect(host=HOST, passwd=PASSWD, db=DB, user=USER)
    sql = 'SELECT * FROM someTable WHERE City = "Melbourne"'
    df = sql.read_frame(sql, con)

4.14 - Saving and Transporting Objects
----------------------------------------------------------------------

R::

    #

Python::

    #

5 - Data Structures
======================================================================

5.1 - Appending Data to a Vector
----------------------------------------------------------------------

R::

    v <- c(v, newItems)
    # OR if single item.
    v[length(v) + 1] <- newItem

Python::

    v = np.append(v, newItems)
    v = np.append(v, newItem)

5.2 - Inserting Data into a Vector
----------------------------------------------------------------------

R::

    # append(v, newValues, after=n)
    append(1:10, 99, after=5)

Python::

    #
    x = np.arange(1, 11)
    x = np.insert(x, 5, 99)

5.3 - Understanding the Recycling Rule
----------------------------------------------------------------------

R::

    #

Python::

    #

5.4 - Creating a Factor (Categorical Variable)
----------------------------------------------------------------------

R::

    #

Python::

    #

5.5 - Combining Multiple Vectors into One Vector and a Factor
----------------------------------------------------------------------

R::

    #

Python::

    #

5.6 - Creating a List
----------------------------------------------------------------------

R::

    #

Python::

    #

5.7 - Selecting List Elements by Position
----------------------------------------------------------------------

R::

    #

Python::

    #

5.8 - Selecting List Elements by Name
----------------------------------------------------------------------

R::

    #

Python::

    #

5.9 - Building a Name/Value Association List
----------------------------------------------------------------------

R::

    #

Python::

    #

5.10 - Removing an Element from a List
----------------------------------------------------------------------

R::

    #

Python::

    #

5.11 - Flatten a List into a Vector
----------------------------------------------------------------------

R::

    #

Python::

    #

5.12 -  Removing NULL Elements from a List
----------------------------------------------------------------------

R::

    #

Python::

    #

5.13 - Removing List Elements Using a Condition
----------------------------------------------------------------------

R::

    #

Python::

    #

5.14 - Initializing a Matrix
----------------------------------------------------------------------

R::

    vec = 1:6
    matrix(vec, 2, 3)

Python::

    x = np.arange(1, 7)
    x.reshape(2, 3)

5.15 - Performing Matrix Operations
----------------------------------------------------------------------

R::

    # transpose.
    t(A)

    # inverse
    solve(A)

    # identity matrix.
    diag(n)

Python::

    # transpose.
    A.T

    # inverse of numpy array
    np.linalg.inv(A)
    # inverse of matrix
    A.I

    # identity matrix.
    np.eye(n)
    # same?
    np.identity(n)

5.16 - Giving Descriptive Names to the Rows and Columns of a Matrix
----------------------------------------------------------------------

R::

    #

Python::

    #

5.17 - Selecting One Row or Column from a Matrix
----------------------------------------------------------------------

R::

    #

Python::

    #

5.18 - Initializing a Data Frame from Column Data
----------------------------------------------------------------------

R::

    #

Python::

    #

5.19 - Initializing a Data Frame from Row Data
----------------------------------------------------------------------

R::

    #

Python::

    #

5.20 - Appending Rows to a Data Frame
----------------------------------------------------------------------

R::

    #

Python::

    #

5.21 - Preallocating a Data Frame
----------------------------------------------------------------------

R::

    #

Python::

    #

5.22 - Selecting Data Frame Columns by Position
----------------------------------------------------------------------

R::

    #

Python::

    #

5.23 - Selecting Data Frame Columns by Name
----------------------------------------------------------------------

R::

    #

Python::

    #

5.24 - Selecting Rows and Columns More Easily
----------------------------------------------------------------------

R::

    #

Python::

    #

5.25 - Changing the Names of Data Frame Columns
----------------------------------------------------------------------

R::

    #

Python::

    #

5.26 - Editing a Data Frame
----------------------------------------------------------------------

R::

    #

Python::

    #

5.27 - Removing NAs from a Data Frame
----------------------------------------------------------------------

R::

    #

Python::

    #

5.28 - Excluding Columns by Name
----------------------------------------------------------------------

R::

    #

Python::

    #

5.29 - Combining Two Data Frames
----------------------------------------------------------------------

R::

    #

Python::

    #

5.30 - Merging Data Frames by Common Column
----------------------------------------------------------------------

R::

    #

Python::

    #

5.31 - Accessing Data Frame Contens More Easily
----------------------------------------------------------------------

R::

    #

Python::

    #

5.32 - Converting One Atomic Value into Another
----------------------------------------------------------------------

R::

    #

Python::

    #

5.33 - Converting One Structured Data Type into Another
----------------------------------------------------------------------

R::

    #

Python::

    #

6 - Data Transformations
======================================================================

6.1 - Splitting a Vector into Groups
----------------------------------------------------------------------

R::

    #

Python::

    #

6.2 - Applying a Function to Each List Element
----------------------------------------------------------------------

R::

    #

Python::

    #

6.3 - Applying a Function to Every Row
----------------------------------------------------------------------

R::

    #

Python::

    #

6.4 - Applying a Function to Every Column
----------------------------------------------------------------------

R::

    #

Python::

    #

6.5 - Applying a Function to Groups of Data
----------------------------------------------------------------------

R::

    #

Python::

    #

6.6 - Applying a Function to Groups of Rows
----------------------------------------------------------------------

R::

    #

Python::

    #

6.7 - Applying a Function to Parallel Vectors or Lists
----------------------------------------------------------------------

R::

    #

Python::

    #

7 - Strings and Dates
======================================================================

7.1 - Getting the Length of a String
----------------------------------------------------------------------

R::

    #

Python::

    #

7.2 - Concatenating Strings
----------------------------------------------------------------------

R::

    #

Python::

    #

7.3 - Extracting Substrings
----------------------------------------------------------------------

R::

    #

Python::

    #

7.4 - Splitting a String According to a Delimiter
----------------------------------------------------------------------

R::

    #

Python::

    #

7.5 - Replacing Substrings
----------------------------------------------------------------------

R::

    #

Python::

    #

7.6 - Seeing the Special Characters in a String
----------------------------------------------------------------------

R::

    #

Python::

    #

7.7 - Generating All Pairwise Combinations of Strings
----------------------------------------------------------------------

R::

    #

Python::

    #

7.8 - Getting the Current Date
----------------------------------------------------------------------

R::

    #

Python::

    #

7.9 - Converting a String into a Date
----------------------------------------------------------------------

R::

    #

Python::

    #

7.10 - Converting a Date into a String
----------------------------------------------------------------------

R::

    #

Python::

    #

7.11 - Converting Year, Month, and Day into a Date
----------------------------------------------------------------------

R::

    #

Python::

    #

7.12 - Getting the Julian Date
----------------------------------------------------------------------

R::

    #

Python::

    #

7.13 - Extracting the Parts of a Date
----------------------------------------------------------------------

R::

    #

Python::

    #

7.14 - Creating a Sequence of Dates
----------------------------------------------------------------------

R::

    #

Python::

    #

8 - Probability
======================================================================

8.1 - Counting the Number of Combinations
----------------------------------------------------------------------

R::

    #

Python::

    #

8.2 - Generating Combinations
----------------------------------------------------------------------

R::

    #

Python::

    #

8.3 - Generating Random Numbers
----------------------------------------------------------------------

R::

    #

Python::

    #

8.4 - Generating Reproducible Random Numbers
----------------------------------------------------------------------

R::

    #

Python::

    #

8.5 - Generating a Random Sample
----------------------------------------------------------------------

R::

    #

Python::

    #

8.6 - Generating Random Sequences
----------------------------------------------------------------------

R::

    #

Python::

    #

8.7 - Randomly Permuting a Vector
----------------------------------------------------------------------

R::

    #

Python::

    #

8.8 - Calculating Probabilities for Discrete Distributions
----------------------------------------------------------------------

R::

    #

Python::

    #

8.9 - Calculating Probabilities for Continuous Distributions
----------------------------------------------------------------------

R::

    #

Python::

    #

8.10 - Converting Probabilities to Quantiles
----------------------------------------------------------------------

R::

    #

Python::

    #

8.11 - Plotting a Density Function
----------------------------------------------------------------------

R::

    #

Python::

    #

9 - General Statistics
======================================================================

9.1 - Summarizing Your Data
----------------------------------------------------------------------

R::

    #

Python::

    #

9.2 - Calculating Relative Frequencies
----------------------------------------------------------------------

R::

    #

Python::

    #

9.3 - Tabulating Factors and Creating Contingency Tables
----------------------------------------------------------------------

R::

    #

Python::

    #

9.4 - Testing Categorical Variables for Independence
----------------------------------------------------------------------

R::

    #

Python::

    #

9.5 - Calculating Quantiles (and Quartiles) of a Dataset
----------------------------------------------------------------------

R::

    #

Python::

    #

9.6 - Inverting a Quantile
----------------------------------------------------------------------

R::

    #

Python::

    #

9.7 - Converting Data to Z-Scores
----------------------------------------------------------------------

R::

    #

Python::

    #

9.8 - Testing the Mean of a Sample (t Test)
----------------------------------------------------------------------

R::

    #

Python::

    #

9.9 - Forming a Confidence Interval for a Mean
----------------------------------------------------------------------

R::

    #

Python::

    #

9.10 - Forming a Confidence Interval for a Median
----------------------------------------------------------------------

R::

    #

Python::

    #

9.11 - Testing a Sample Proportion
----------------------------------------------------------------------

R::

    #

Python::

    #

9.12 - Forming a Confidence Interval for a Proportion
----------------------------------------------------------------------

R::

    #

Python::

    #

9.13 - Testing for Normality
----------------------------------------------------------------------

R::

    #

Python::

    #

9.14 - Testing for Runs
----------------------------------------------------------------------

R::

    #

Python::

    #

9.15 - Comparing the Means of Two Samples
----------------------------------------------------------------------

R::

    #

Python::

    #

9.16 - Comparing the Locations of Two Samples Nonparametrically
----------------------------------------------------------------------

R::

    #

Python::

    #

9.17 - Testing a Correlation for Significance
----------------------------------------------------------------------

R::

    #

Python::

    #

9.18 - Testing Groups for Equal Proportions
----------------------------------------------------------------------

R::

    #

Python::

    #

9.19 - Performing Pairwise Comparisions Between Group Means
----------------------------------------------------------------------

R::

    #

Python::

    #

9.20 - Testing Two Samples for the Same Distribution
----------------------------------------------------------------------

R::

    #

Python::

    #


10 - Graphics
======================================================================

10.1 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.2 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.3 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.4 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.5 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.6 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.7 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.8 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.9 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.10 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.11 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.12 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.13 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.14 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.15 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.16 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.17 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.18 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.19 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.20 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.21 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.22 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.23 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.24 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.25 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.26 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.27 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.28 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

10.29 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #


11 - Linear Regression and ANOVA
======================================================================

11.1 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.2 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.3 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.4 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.5 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.6 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.7 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.8 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.9 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.10 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.11 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.12 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.13 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.14 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.15 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.16 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.17 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.18 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.19 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.20 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.21 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.22 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.23 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

11.24 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12 - Useful Tricks
======================================================================

12.1 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.2 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.3 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.4 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.5 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.6 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.7 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.8 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.9 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.10 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.11 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.12 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.13 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.14 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.15 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.16 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.17 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.18 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

12.19 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #


13 - Beyond Basic Numerics and Statistics
======================================================================

13.1 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

13.2 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

13.3 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

13.4 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

13.5 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

13.6 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

13.7 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

13.8 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

13.9 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #


14 - Time Series Analysis
======================================================================

14.1 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.2 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.3 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.4 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.5 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.6 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.7 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.8 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.9 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.10 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.11 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.12 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.13 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.14 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.15 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.16 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.17 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.18 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.19 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.20 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.21 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.22 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

14.23 - XXX
----------------------------------------------------------------------

R::

    #

Python::

    #

