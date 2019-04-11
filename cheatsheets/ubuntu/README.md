# Ubuntu/Bash Commands

Check which JDK packages are installed

```bash
sudo dpkg --list | grep -i jdk
```

Monitor performance for only some specific processes

```bash
top -p `pgrep "java"`
```

Show only some specific processes

```bash
ps -ef | grep "<process name>"
```

Find public ip address

```bash
curl  ifconfig.me
```
