When you just get a generic error:
![[Pasted image 20260710075425.png]]

it is possible the root policy packages are corrupted:
First it is advised to create a backup of the config and after the backup run the command and say y this will restore the fortimanager config
diagnose cdb check policy-packages root