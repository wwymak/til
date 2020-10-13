# Writing a bash script in python

It's really easy to do, just putting it here for handy reference.

As an example, it's often quite convienent using `wget` to download files rather than having to faff around with python request libraries. If you have a whole list of files to download, you can create a bash script that does all the `wget` for you, e.g.

```python

download_urls_commands = [f"wget -N {x}" for x in set(list_of_urls)]

with open(f"fetch_urls.sh", "w") as f:
    f.write("#!/bin/bash")
    f.write("\n")
    for line in download_urls_commands:
        f.write(line)
        f.write("\n")
```
