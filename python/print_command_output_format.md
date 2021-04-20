# Adding formatting to print outputs

It can be useful to have bold/italic text and/or colors from a `print` output. The relevant code to do so is:

```python
class Color:
   PURPLE = '\033[95m'
   CYAN = '\033[96m'
   DARKCYAN = '\033[36m'
   BLUE = '\033[94m'
   GREEN = '\033[92m'
   YELLOW = '\033[93m'
   RED = '\033[91m'
   BOLD = '\033[1m'
   UNDERLINE = '\033[4m'
   END = '\033[0m'

print(f"{Color.BOLD}Hello World !{color.END}")
```

Courtesy of https://stackoverflow.com/a/17303428/11956075