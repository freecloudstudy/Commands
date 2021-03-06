## <p align="center"><ins>DCUI Console Keys</ins></p>
<div align="center">

| Description | Shortcuts|
| :--- | :--- |
| Switches to the esxi shell| ***ALT+F1***|
| Switches to the DCUI| ***ALT+F2***|
| Returns to the banner screen| ***ALT+F11***|
| Displays the VMkernel log on the console| ***ALT+F12***|


## <p align="center"><ins>System related commands</ins></p>

| Description | Command |
| :--- | :--- |
| ESXi build and version numbers | ***esxcli system version get*** <br /> ***vmware -vl*** |
| Hostname, domain and FQDN for the host | ***esxcli system hostname get*** |
| Date and Time of when ESXi was installed | ***esxcli system stats installtime get*** |
| Lists the local users created on the ESXi host | ***esxcli system account list*** |
| To enter maintenance Mode | ***esxcli system maintenanceMode set –enable true*** |
| To exit maintenance Mode | ***esxcli system maintenanceMode set –enable false*** |
| To Check the maintenance Mode Status | ***esxcli system maintenanceMode get*** |
| VIB Installation version in ESXi  | ***esxcli software vib list*** |

## <p align="center"><ins>ESXTOP</ins></p>

| Description | Command |
| :--- | :--- |
|ESXTOP- Batch Mode|***esxtop -b -d 2 -n 100 > esxtop.csv***<br/><br/>b=batch mode<br/>d=delay<br/>n=No of Iterations<br/>a=all Metrics|

## <p align="center"><ins>Storage</ins></p>

| Description | Command |
| :--- | :--- |
| get the naa_id or label_name of the Datastore/LUN | ***esxcli storage core path list***<br /> ***esxcli-scsidevs -l*** <br /> ***esxcli storage vmfs extent list*** <br/>***esxcli storage filesystem list***|
| get the list of permanently detached devices | ***esxcli storage core device detached list*** |
| verify the device status | ***esxcli storage core device list -d <NAA ID>naa_id***|
| detach a device/LUN | ***esxcli storage core device set --state=off -d naa_id*** |
| Permanently remove the device configuration <br/>information from the system | ***esxcli storage core device detached remove -d naa.id***|
| rescan hba for LUNS\Storage | ***esxcli storage core adapter rescan -A vmhbaX \| –all*** |
| Unmount the datastore | ***esxcli storage filesystem unmount -u uuid \| -l lable \| -p path***<br/><br/> <ins>examples:</ins> <br/> ***esxcli storage filesystem unmount -l LUN01*** <br/> ***esxcli storage filesystem unmount -u 4e414917-a8d75514-6bae-0019b9f1ecf4*** <br/> ***esxcli storage filesystem unmount -p /vmfs/volumes/4e414917-a8d75514-6bae-0019b9f1ecf4***|

## <p align="center"><ins>Network</ins></p>

| Description | Command |
| :--- | :--- |
| Status of the ESXi firewall | ***esxcli network firewall get*** |
| List of all enabled firewall rules on ESXi | ***esxcli network firewall ruleset list*** |
| Displays the IPv4 configuration for all the interfaces present on ESXi | ***esxcli network ip interface ipv4 get*** |
| List of Physical Uplinks | ***esxcli network nic list*** |
| VMware’s ifconfig | ***esxcli network ip interface list*** |
| VMware’s netstat | ***esxcli network ip connection list*** |
| Networking info about the VMs | ***esxcli network vm list*** |
| Get an uplink stats | ***esxcli network nic stats get -n vmnic1*** |
| Get the Netqueue stats | ***vsish -e get /net/pNics/vmnic1/stats*** |
| Get the driver info | ***esxcli network nic get -n vmnic#*** |
| Test Connectivity of vmk uplink | ***vmkping ++netstack=vxlan -s PacketSize -d -I vmkX Destination*** |

## <p align="center"><ins>Important urls</ins></p>

| Description | urls|
| :--- | :--- |
| esxtop Guide | ***https://www.virten.net/vmware/esxtop/*** |
| vscsiStats   | ***http://www.yellow-bricks.com/2009/12/17/vscsistats/***<br /> ***http://www.gabesvirtualworld.com/converting-vscsistats-data-into-excel-charts/***|
|How to Remove Storage Devices from ESXi Hosts|***https://lazyadminblog.com/2015/11/21/how-to-remove-storage-devices-from-esxi-hosts/***|
 
</div>

## <p align="center"><ins>Important Notes</ins></p>
- localcli commands are equivalent to ESXCLI commands, but bypass hostd. The localcli commands are only for situations when hostd is unavailable and cannot be restarted. After you run a localcli command, you must restart hostd. Run ESXCLI commands after the restart.Warning: If you use a localcli command in other situations, an inconsistent system state and potential failure can result.