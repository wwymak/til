# How to say yes to terminal prompts

Some inbuilt functions in ubuntu e.g. apt-get install have the `-y` option to bypass the `do you want to do x` prompt. However, if the command don't have this option (e.g. `rm *.txt`), and you don't want to manually press `y` for a few thousand txt files, you can use the `yes` command e.g. `yes | rm *.txt`. (the `yes` basically send a continuous stream of `yes` to the terminal https://www.computerhope.com/unix/yes.htm)
