# Ubuntu/Bash Commands

List hidden directories

```bash
ls -ld .?*
```

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
curl ifconfig.me
```

Show ubuntu version

```bash
lsb_release -a
```

## apt

Show installed version of package

```bash
apt list <package_name>
```

## Windows Subsystem for Linux

Restart Ubuntu subsystem

```bash
#  Using CMD (Administrator)
net stop LxssManager
net start LxssManager
```
