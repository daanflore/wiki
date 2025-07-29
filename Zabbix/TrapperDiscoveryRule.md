# Trapper based discovery rule

First you need to create a discovery rule 

The type of the rule neerd to be a zabbix trapper and the key will be used to push the data for the host using the zabbix_sender:

![trapperBasedDiscovery.png](.\trapperBasedDiscovery.png)


Once you have created your discovery rule you can create item prototypes.
In these prototypes you can refer to data you send to your discovery rule.
This is done with {#Key} notation.

In this example semanticModelId is fed from the discovery rule and clientId is fed from a macro

![itemPrototype.png](.\itemPrototype.png)

Now we can assign the template to a host in zabbix.

First we need to build a json that zabbix is able to read and parse for the discovery rule.
This needs to follow the following structure where the object in the `data` array should contain the key names like you defined in your item prototype 
```json
{
	"data": [
		{
			"{#SEMANTICMODELNAME}": "Test dataset",
			"{#SEMANTICMODELID}": "Dateset ID"
		},
		{
			"{#SEMANTICMODELNAME}": "Second dataset",
			"{#SEMANTICMODELID}": "Second dataset ID"
		}
	]
}
```

To send this info to zabbix we can use the following command:

```bash
echo '[Full zabbix host name] [key defined in the discovery rule] [Flattend json] |  zabbix_sender -z zabbixServerName -i -
```
in our case this transaltes to:
```bash
echo 'local.BiChecker PowerBiDatasets {"data":[{"{#SEMANTICMODELNAME}":"Test dataset","{#SEMANTICMODELID}":"Dateset ID"},{"{#SEMANTICMODELNAME}":"Second dataset","{#SEMANTICMODELID}":"Second dataset ID"}]} |  zabbix_sender -z zabbixController -i -
```

> **_NOTE:_**  echo writed to the default output, | pass the output of the echo to the next command, - means the standard input in this case the result of the echo.


