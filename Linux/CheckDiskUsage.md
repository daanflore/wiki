# NCDU

[site](https://dev.yorhel.nl/ncdu)

Tool that allows you to scan the usage of a disk on a server

``` bash
sudo ncdu .
```


>  **_NOTE:_**  In linux when you delete a file it is possible that it was still in use by a process and then it will not be removed until the program releases it
> You can check this using  lsof or the clasic way find sudo find /proc/*/fd -lname 'name of removed file'


You can recognize deleted entries as they have a (deleted) flag at the end:
```sh 
sudo lsof | grep -i delete
[sudo] password for dafl: 
test 2980065                        root  txt       REG              253,5  87114784        137 /tmp/846e3f8e-25e8-494a-a515-69138599c10c (deleted)
test 2980103                        root  txt       REG              253,5  87114784        138 /tmp/25b7ef99-c779-47f0-b1f5-184e7fa5c620 (deleted)
test 3038419                        root  txt       REG              253,5  87114784        147 /tmp/7da97b9a-1ec0-4e0c-ab20-359ad2768e13 (deleted)
test 3065245                        root  txt       REG              253,5  87114784        145 /tmp/9c3d2b75-3301-4310-80b7-8097fa7b080f (deleted)
test 3070219                        root  txt       REG              253,5  87114784        146 /tmp/03140ced-a2e0-4c86-ba53-eae4cc369b41 (deleted)
```