# NCDU

[site](https://dev.yorhel.nl/ncdu)

Tool that allows you to scan the usage of a disk on a server

``` bash
sudo ncdu .
```


>  **_NOTE:_**  In linux when you delete a file it is possible that it was still in use by a process and then it will not be removed until the program releases it
> You can check this using  lsof or the clasic way find sudo find /proc/*/fd -lname 'name of removed file'


