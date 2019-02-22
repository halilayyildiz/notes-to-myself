# GIT Commands

## Basic  Commands

Show status

```bash
git status
```

Show actual branch

```bash
git branch
```

Find specific files and run some command 

```bash
 find . -name '*.sh' -exec echo {} \;
```

Find public ip address

```bash
curl  ifconfig.me
```

## Advanced Commands

Make file executable

```bash
git update-index --chmod=+x <path/to/file>
```