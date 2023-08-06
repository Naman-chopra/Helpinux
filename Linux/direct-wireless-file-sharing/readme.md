# Share files without any 3rd party services!!
Hello there! here's a short and easy tutorial that might be useful to share files with people on the same wireless network.
## How to do it?
Trust me, this is going to be a very simple, short and fun hack to implement.
 Files are generally shared (wirelessly) by creating a server that can provide files to the people who request them. We are going to do something similar.

### `Caution: The server that we'll create will have no security so it is recommended that you provide your IP to trusted people only`

## Let's check the requirements
In your console run the following commands one by one:
```console
sudo apt install python3
sudo apt install net-tools
python3 --version
ifconfig
```
Note down your IP (it would be similar to the output below where wlp4s0 is my network interface)
```console
wlp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet "IP ADDRESS HERE"  netmask 255.255.224.0  broadcast 172.16.95.255
        inet6 "IPV6 HERE"  prefixlen 64  scopeid 0x20
        RX packets 7479414  bytes 1475065412 (1.3 GiB)
        RX errors 0  dropped 13  overruns 0  frame 0
        TX packets 149440  bytes 47739862 (45.5 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
Now suppose you want to serve a directory called `Files_to_share` that is in your home directory, In the console, type:
``` console
cd /home/USERNAME/Files_to_share
python3 -m http.server 50001
```
Now on your friend's browser type `yourIP:50001`. For egs if your IP is 123.123.123.123, in your friend's browser's search bar type `123.123.123.123:50001`.
*NOTE: You both should be connected to the same wireless network for this to work*

## How to download the files??
The procedure uptil now could allow any user to access the files in your directory, but what if they want to download them? Assuming your friend is a linux user, ask him to type in the terminal:
```console
wget -r "http://123.123.123.123:50001"
```
This will download the files to your friend's device

### For regular people:::::
We can use this life hack above and use it with the previous alias-customisation life hack.
just add another entry to the bashrc file like so:
```console
alias serve='python3 -m http.server 50001'
```
And now you can turn the server on just by typing `serve` on your CLI
