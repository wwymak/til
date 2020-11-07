# How to fill np.nan values in numpy arrays with values

Pandas has a handy `.fillna(x)` function, but there is no equivalent in numpy arrays. To do this, we first define a mask where the nans are , then create a masked array with the masked array, then use the [`fix_invalid` function](https://numpy.org/doc/stable/reference/generated/numpy.ma.fix_invalid.html?highlight=fix_invalid#numpy.ma.fix_invalid) in numpy like so:


```python
import numpy as np

# original_arr contains np.nans
# find where the nans are
mask = np.isnan(original_arr)
idx = np.where(~mask)

# create a np masked array with the mask and a fill value for the invalid values (ie nan)
new_array = np.ma.array(original_arr, mask = mask, fill_value=-10)
# use the fix_invalid function to fillna, then use .data to turn the masked array back to normal numpy array
new_array = np.ma.fix_invalid(new_array).data

```
