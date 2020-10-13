# Reading a text file into a string variable

Using `pathlib`, this is literally a one liner, e.g.

```python
from pathlib import Path
my_variable = Path('data.txt').read_text()
```

the file can be _any_ text file, so e.g. if you want to read a sql file into python to query a database using sqlalchemy/google cloud sdk etc, you can use the same command to do so
