# Troubleshooting

### Error: Too many open files

Increase open file descriptiors limit.  You may set it for one time \(before reboot\), by command:

```text
ulimit -n 65535
```

For all time change, put string

```text
* soft nofile 65535
```

to file /etc/security/limits.conf . You can get more information about it in OS docs.

