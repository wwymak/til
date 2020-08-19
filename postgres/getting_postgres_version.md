# Finding the running postgres version without connecting
Recently, I had issues connecting to my local postgres instance because of password config issues (more on that another time). According to various discussions on stack overflow, I need to change my pg_hba.conf, but after many attempts with no luck, I realised that I have both postgres 11 and 12 under `/etc/postgresql`. I was tweaking the conf under version 11, So I am most likely to be changing the conf for the wrong postgres version. As it turns out, to check which version is actually running is really easy, just do

`psql --version`

which spits out the postgresql database version (and not the psql client, or the client version go in step with the server). In any case, it says `psql (PostgreSQL) 12.2`. Once I fixed the config under 12, I am back up and running again. 
