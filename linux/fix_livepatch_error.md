# Fixing Ubuntu's Livepatch error

Ubuntu comes with Livepatch to keep your software updated. You usually see a green tick on the shield icon on the top tray. However, once in a while, it will show an error, and on launching the Livepatch settings, I see:

```
Canonical Livepatch has experienced an internal error. Please refer to https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues for further information.
```

Fixing this is fairly simple, just do, as per [this SO thread](https://askubuntu.com/questions/1150844/canonical-livepatch-informs-about-internal-error-what-to-do):

`sudo canonical-livepatch refresh`

(this error might be something to do with an unstable connection when booting...)
