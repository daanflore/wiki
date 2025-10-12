## chrooted ssh:

User hun root wordt aangepast naar de niet default locatie
Config van chroot kan je terug vinden in de /etc/ssh/sshd_config

```bash
Match User sftpuser
    ChrootDirectory /sftp/chroot/%u
    ForceCommand internal-sftp
    AllowTcpForwarding no
    X11Forwarding no
```