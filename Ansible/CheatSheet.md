# CheatSheet
Run a playbook
```bash
ansible-playbook [path to playbook] { --vault-password-file [vault fullname] } { --limit "[servername/ group name or regex]" }
```
 

Run a one of command
```bash
ansible --limit "[servername/ group name or regex]" -m shell "[command to run on the servers]" [--become]
```

