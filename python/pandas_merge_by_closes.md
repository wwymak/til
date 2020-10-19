# Merge pandas dataframe by closest value

To merge two dataframes by closest value on the join key rather than exact value, `pd.merge_asof` is super handy. e.g. `df1` contains timestamps in which events happen, and `df2` has the timestamps of events type2, which occur less frequently. You want to know which event2 correspond to the events in df1, you can use a merge_asof join to match the two dataframes, even if the timestamp columns doesn't match exactly.

Full details at https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.merge_asof.html
