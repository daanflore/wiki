
Run a playbook
```bash
ansible-playbook [path to playbook] { --vault-password-file [vault fullname] } { --limit "[servername/ group name or regex]" }
```
 
Run a one of command

an exclude can be done using ! before the filter and : can be used to add miltiple filters
```bash
ansible "[servername/ group name or regex]" -m shell -a "[command to run on the servers]" [--become]

'partialMatch*:!groupvar'
```

List all variables for a host:

```bash
ansible "[servername/ group name or regex]" -m setup
```


List all hosts that will be targeted by a commend:
```shell
ansible '[servername/ group name or regex]' --list-hosts
```
