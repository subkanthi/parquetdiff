# parquetdiff
Parquet Diff to diff Parquet files in python

Inspired by jsondiff
https://github.com/ZoomerAnalytics/jsondiff

Very good article to explain Parquet format.
https://www.kaggle.com/residentmario/notes-on-apache-parquet

This is a simple utility that uses pyarrow to load
the parquet file into a dataframe and it does a diff
between dataframe.

The easiest combination would be to use pandas together with pyarrow. Once you have both packages installed, you can use https://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_parquet.html to load the Apache Parquet file into a Pandas DataFrame and then use Pandas' assert_frame_equal on the two resulting DataFrames.

Note that this will compare the two resulting DataFrames and not the exact contents of the Parquet files. As not all Parquet types can be matched 1:1 to Pandas, information like if it was a Date or a DateTime will get lost but Pandas offers a really good comparison infrastructure.

Alternatively, you could utilise Apache Arrow (the pyarrow package mentioned above) and read the data into pyarrow.Table and check for equality. This method preserves the type information much better but is less verbose on the differences if there are some:

import pyarrow.parquet as pq

table1 = pq.read_table('file1.parquet')
table2 = pq.read_table('file2.parquet')

assert table1.equals(table2)
