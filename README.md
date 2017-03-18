# vl
vl is short for "virtual machine login" It enables management of virtual
machines running on a remote SmartOS node. To use this command type vl followed
by enough text to uniquely identify the virtual machine that you want to
login to.

## Examples

When run with no parameters it outputs a list of virtual machines:
````
greg@home$ vl
UUID                                  TYPE  RAM      STATE             ALIAS
aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee  LX    512      running           prod-samba
aaaaaaaa-bbbb-cccc-dddd-ffffffffffff  LX    512      running           prod-nginx-01
aaaaaaaa-bbbb-cccc-dddd-gggggggggggg  LX    512      running           prod-nginx-02
greg@home$
````

When run with a parameter it logs into the virtual machine that is the closest match for your input.
````
greg@home$ vl samba
[Connected to zone 'aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee' pts/3]
root@prod-samba:#
````
````
greg@home$ vl nginx-01
[Connected to zone 'aaaaaaaa-bbbb-cccc-dddd-ffffffffffff' pts/3]
root@prod-nginx-01:#
````
````
greg@home$ vl nginx
More than one virtual machine matches nginx. Here are your choices:
aaaaaaaa-bbbb-cccc-dddd-ffffffffffff  LX    512      running           prod-nginx-01
aaaaaaaa-bbbb-cccc-dddd-gggggggggggg  LX    512      running           prod-nginx-02
greg@home$
````

## Configuration
Before using this script you will need to set a shell variable to tell the script the address of your SmartOS machine:
Place the following line in your ~/.profile or run it from the command line (replace the ip address with your SmartOS host address):
````
export SMARTOS=192.168.1.10
````
