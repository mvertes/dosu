# dosu

Switch user then execute a command.

Usage: `dosu user command [args...]`

The command will not run in a child process, but will be executed
in place, thus avoiding TTY and signal propagation issues in docker
entry points.

```
$ docker run -ti --rm alpine:edge su -c 'ps aux'
PID   USER     TIME   COMMAND
    1 root       0:00 ash -c ps aux
	6 root       0:00 ps aux
$ docker run -ti --rm -v $PWD/dosu:/sbin/dosu alpine:edge dosu root ps aux
PID   USER     TIME   COMMAND
    1 root       0:00 ps aux
```

## Why reinvent gosu ?

It takes 174 bytes of portable shell instead of 1.8 MB of binary code.

## License

[ISC License](./LICENSE)
