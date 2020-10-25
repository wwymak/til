# Reclaiming disk space from (ana)conda

Conda seems to do some internal caching which means it can end up hogging all your disk space with not really needed cache files: uses

`conda clean --all`

to remove these files. (I managed to reclaim > 40 GB using this...)
