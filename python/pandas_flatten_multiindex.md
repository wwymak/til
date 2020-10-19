# Convert pandas multindex groupby to flattened columns

If you do a groupby , and have ['min', 'max'] aggregations on many output columns (e.g. `df.groupby('a')['b', 'c'].agg(['min', 'mean', 'max'])`), you would end up with a multindex on the columns which can be inconvenient to access. Convert them like so:

```python
grouped = df.groupby('a')['b', 'c'].agg(['min', 'mean', 'max'])
grouped.columns = [f"{x}_{y}" for x, y in grouped.columns.to_flat_index()]
grouped = grouped.reset_index()
```

now grouped will have columns: `['a', 'b_min', 'b_mean', 'b_max' , 'c_min', 'c_mean', 'c_max']`
