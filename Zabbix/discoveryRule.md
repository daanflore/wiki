# Zabbix discovery rule

[Custom LLD rules](https://www.zabbix.com/documentation/current/en/manual/discovery/low_level_discovery/custom_rules)

script that will discover the entries
```bash
#!/bin/bash

service_list=$(systemctl list-unit-files | grep -E '\.(service|automount)\s+enabled' | sed -e 's/[[:blank:]]\+enabled.*//' -e 's/\.service//')


[[ -r /etc/zabbix/zbx_service_discovery_ignore ]] && {
    service_list=$(echo "$service_list" | grep -Ev -f /etc/zabbix/zbx_service_discovery_ignore)
}
echo -n '{"data":[';for s in ${service_list}; do echo -n "{\"{#SERVICE}\": \"$s\"},";done | sed -e 's:\},$:\}:';echo -n ']}'

```

Tell ansible to run the file:
```bash
UserParameter=systemd.service.discovery,/usr/local/bin/zbx_service_discovery.sh
```

Linux file location:
/etc/zabbix/zabbix_agentd.d/userparameter.conf

The script should return the data in the following format
```json
{
    "data": [
        {
            "{#NameOfKey}": "value",
         	"{#NameOfKey2}": "other value"
        },
        ...
    ]
}
```

Use Zabbix trapper to allow pushing data to it as a discovery rule
