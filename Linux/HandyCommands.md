# Handy commands

To run a script as a different user you can make use of the runuser command:
```bash
sudo runuser -u [username] -- [script]
```
run command in background

& make it that the command runs in the background
```bash
nohup ansible-playbook playbooks/playbook.yml --vault-password-file vaultpass --limit limit  > /tmp/log.log &
```