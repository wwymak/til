# Import functions from a file in a different folder

Let's say you have a project that has folders doing different tasks and one shared folder that have common functionality e.g.

```
my_project
go.mod
|--functionality_1
    |--do_stuff_1.go
|--functionality_2
    |--do_stuff_2.go
|--functionality_3
    |--do_stuff_3.go
|--library
    |--utils.go
```

to import a function, say, `DoTask` from `library` in e.g. `functionality_1.go`, specify the imports like so:

`import lib "my_project/library"` (assuming you have defined go.mod such that it starts with `module module data-csgo-demos`)

Also, remember that to make functions importable in a different file the function must start with Uppercase
