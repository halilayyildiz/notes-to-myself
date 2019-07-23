# Helm

Init tiller

```bash
helm init --history-max 200
```

Update helm repo

```bash
helm repo update
```

## Manage Charts

Create chart

Deploy chart from directory

```bash
helm install --name <chart_name> <path_to_directory>
```

List installed charts

```bash
helm ls
```

List installed charts (included deleted ones)

```bash
helm list -a
```

Update chart from directory

```bash
helm upgrade <chart_name> <path_to_directory>
```

Delete release

```bash
helm delete <chart>
```

Delete chart

```bash
helm delete --purge <chart>
```

Display processed template output

```bash
helm template <chart>
```
