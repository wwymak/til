# Don't refetch file in wget if a copy already exists locally

`wget` is a very convenient way to fetch files from the internet, but for larger files (or if you have a lot of them), you probably only want to fetch if the file don't exist locally or it has changed on the server. To do this is simple: just pass the `-N` option to wget e.g. `wget -N https://www.somefile.gz`

credit https://stackoverflow.com/a/16840827/11956075
