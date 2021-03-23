# combining Matplotlib legends from two axis

In matplotlib you can have a twin axis, ie one left y axis and one right y axis (and also top and bottom x axes).
If you want legends for the data you are plotting on both, it would be useful to have them in 1 box. This is quite 
easy to do 

```python
fig, ax = plt.subplots()

ax.plot(x, y1, '-', label = 'Swdown')
ax.plot(x, y2, '-', label = 'Rn', c='red')
ax2 = ax.twinx()
ax2.scatter(x, y3, label = 'temp', c='green')

# ask matplotlib for the plotted objects and their labels
lines, labels = ax.get_legend_handles_labels()
lines2, labels2 = ax2.get_legend_handles_labels()
ax2.legend(lines + lines2, labels + labels2, loc=0)
```

courtesy https://stackoverflow.com/a/10129461/11956075