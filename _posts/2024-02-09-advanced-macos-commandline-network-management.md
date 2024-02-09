## macOS and advanced network commands for managing DNS settings

While MDM is unequivocally a must for managing macOS at (really any) scale, there are times when a scripted approach can still be needed.

### Commands for determining the active network interface and working with DNS server settings:

When we want to programmatically determine the existing primary network interface ID, name and existing DNS servers, there are a few different ways we can go about this:

```shell
serviceGUID="$(printf "open\nget State:/Network/Global/IPv4\nd.show" | /usr/sbin/scutil | /usr/bin/awk '/PrimaryService/{print $3}')"

serviceName="$(printf "open\nget Setup:/Network/Service/${serviceGUID}\nd.show" | /usr/sbin/scutil | /usr/bin/awk -F': ' '/UserDefinedName/{print $2}')"
```

!!! OR !!!

```shell
activeIF=$(route -n get 0.0.0.0 2>/dev/null | awk '/interface: / {print $2}')

serviceName=$(networksetup -listnetworkserviceorder | grep "$activeIF" | awk -v FS="(Hardware Port: |,)" '{print $2}')

```
#### The problem with cataloging existing DNS servers, when they are supplied via DNS

When the DNS servers are provided via DHCP, a problem with the common approach for getting that info,
will fail:

```shell
/usr/sbin/networksetup -getdnsservers "serviceName"
```

Will come back with: "There aren't any DNS Servers set on \<serviceName\>"

Which is hardly useful ! So, we can proceed with the following:

```shell
declare currDNS=($(/usr/sbin/networksetup -getdnsservers "serviceName"))

if [[ ${currDNS[0]} == "There" ]]; then
  declare currDNS=($(ipconfig getsummary $activeIF | awk -v FS="({|, |})" '/domain_name_server/ {$1=""; print $0 }'))
fi

# check the array, via 
# declare -p currDNS
# For an example of working with the captured info:
# echo ${currDNS[1]}

# So now you can capture those existing DNS servers and append another

/usr/sbin/networksetup -setdnsservers "$serviceName" ${currDNS[1]} ${currDNS[2]} 8.8.8.8
```

#### Originally published by me, Feb 9th, 2024
