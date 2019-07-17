# parquetdiff
Parquet Diff to diff Parquet files in python

Inspired by jsondiff
https://github.com/ZoomerAnalytics/jsondiff

Very good article to explain Parquet format.
https://www.kaggle.com/residentmario/notes-on-apache-parquet

This is a simple utility that uses pyarrow to load
the parquet file into a dataframe and it does a diff
between dataframe.
