
# K9s
terminal based management app

Commands:
```shell
# Connect to known context
k9s

# Connect based on contect you pass
k9s --context [path to a file]
```

# Stern
terminal container log vieuwer
```
stern coredns * --since=12h --only-log-lines -A -t  --kubeconfig [file]
```