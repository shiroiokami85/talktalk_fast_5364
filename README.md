# talktalk_fast_5364
A repository for firmware related to the Talktalk Sagemcom F@st 5364 DSL Router

How to use this for tinkering and exploring the router itself.

Download both firmwares and install the older default firmware 2600t

When the router has rebooted run the following using the developer console in your browser.

$.xmo.setValuesTree(true,"Device/UserAccounts/Users/User[@uid=3]/RemoteAccesses/RemoteAccess[@uid=3]/Enabled")

This will enable SSH 

user and password are admin and whatever your password is to login to the router GUI

after enabling SSH reupgrade to the latest 2816t firmware.

ssh admin@192.168.1.1 your password

to login as root, type login -> user: root -> password: root

Now tinker to your hearts content!

Thanks to DavidBrent over at https://forum.openwrt.org/u/DavidBrent

Disabling automatic updates, Disabling TR-069 since the GUI doesn't actually allow you too

xmo-client -p "Device/ManagementServer/URL" -s ""
xmo-client -p "Device/ManagementServer/TR69InternalData/Settings/Port" -s 0

Turning bridge mode on lan port 1

xmo-client -p "Device/Bridging/Bridges/Bridge[@uid=1]/Ports/Port[@uid=2]/Enable" -s "false"
xmo-client -p "Device/Bridging/Bridges" -a
xmo-client -p "Device/Bridging/Bridges/Bridge[@uid=3]/Ports" -a
xmo-client -p "Device/Bridging/Bridges/Bridge[@uid=3]/Ports" -a
xmo-client -p "Device/Bridging/Bridges/Bridge[@uid=3]/Ports" -a
xmo-client -p "Device/Bridging/Bridges/Bridge[@uid=3]/Enable" -s "true"
xmo-client -p "Device/Bridging/Bridges/Bridge[@uid=3]/Ports/Port[@uid=1]/Enable" -s "true"
xmo-client -p "Device/Bridging/Bridges/Bridge[@uid=3]/Ports/Port[@uid=1]/ManagementPort" -s "true"
xmo-client -p "Device/Bridging/Bridges/Bridge[@uid=3]/Ports/Port[@uid=2]/Enable" -s "true"
xmo-client -p "Device/Bridging/Bridges/Bridge[@uid=3]/Ports/Port[@uid=3]/Enable" -s "true"
xmo-client -p "Device/Bridging/Bridges/Bridge[@uid=3]/Ports/Port[@uid=2]/LowerLayers" -s "Device/Ethernet/Interfaces/Interface[PHY1]"
xmo-client -p "Device/Bridging/Bridges/Bridge[@uid=3]/Ports/Port[@uid=3]/LowerLayers" -s "Device/Ethernet/VLANTerminations/VLANTermination[VLAN_DATA]"
xmo-client -p "Device/IP/Interfaces/Interface[@uid=2]/IPv4Addresses/IPv4Address[@uid=1]/Enable" -s "false"
