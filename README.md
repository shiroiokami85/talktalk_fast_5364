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
