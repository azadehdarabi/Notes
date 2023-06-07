
==**Network-Mask :**==
A network mask, also known as a subnet mask, is a 32-bit binary value used to divide an IP address into two parts: the network address and the host address. The network address identifies the network to which the device belongs, while the host address identifies the specific device on the network.

The network mask consists of a string of 1's followed by a string of 0's, where the number of 1's represents the length of the network address. For example, a network mask of 255.255.255.0 (or /24 in CIDR notation) indicates that the first 24 bits of the IP address represent the network address, while the remaining 8 bits represent the host address.

The network mask is an essential component of IP networking because it helps to define the boundaries of a network. Devices with IP addresses that have the same network address and network mask are considered to be on the same network and can communicate with each other directly. Devices with IP addresses that have different network addresses or network masks must communicate through a router.

Network masks can vary in length from 1 bit to 32 bits, depending on the size of the network. A longer network mask allows for more subnets to be created within a network, while a shorter network mask allows for more devices to be connected to a single subnet. Choosing the appropriate network mask for a network is an important aspect of IP network design, as it can affect the overall performance and security of the network.


==**Default Router:**==
When a device on a network wants to communicate with a device on another network, it sends the traffic to the default router, which then forwards the traffic to the appropriate destination.


==**Interface**:==
In networking, an interface refers to a connection point between a device and a network. An interface can be physical, such as a network card or Ethernet port, or virtual, such as a software-based network interface created by a virtual machine or container.


==**NAT**:==
NAT stands for Network Address Translation. It is a technique used in computer networking to allow devices on a private network to communicate with devices on a public network, such as the internet.

In a typical NAT setup, a router or firewall sits between the private network and the public network. The private network uses IP addresses that are not routable on the public network, such as those in the range 192.168.x.x or 10.x.x.x. When a device on the private network wants to communicate with a device on the public network, it sends a request to the router or firewall. The router or firewall then replaces the private IP address with its own public IP address and forwards the request to the device on the public network. When the device on the public network responds, the router or firewall replaces its own public IP address with the private IP address of the device on the private network and forwards the response back to that device.

NAT allows multiple devices on a private network to share a single public IP address, which can help conserve IP addresses and reduce the need for public IP addresses. It also provides a degree of security, as devices on the private network are not directly accessible from the public network, and incoming traffic can be filtered and controlled at the router or firewall.

There are different types of NAT, including static NAT, dynamic NAT, and port address translation (PAT). In static NAT, a one-to-one mapping is created between a private IP address and a public IP address. In dynamic NAT, a pool of public IP addresses is used and assigned dynamically to devices on the private network. In PAT, a single public IP address is used and different port numbers are assigned to each device on the private network to uniquely identify them.

In summary, NAT is a technique used in computer networking to allow devices on a private network to communicate with devices on a public network. It provides a way to share a single public IP address among multiple devices and provides a degree of security by hiding the private IP addresses from the public network.


==**Route Aggregation:**==
Route aggregation means that an ISP uses a single prefix to advertise multiple networks. Route aggregation is useful because an ISP can use this technique to advertise to the rest of the Internet a single prefix address for the multiple networks that the ISP has.  is a technique used in computer networking to reduce the size of routing tables and improve network performance.


==**Destination-based forwarding:**==
With destination-based forwarding, the match operation of a router looks up only the destination IP address of the to-be-forwarded datagram, and the action operation of the router involves sending the packet into the switching fabric to a specified output port. 


==**Generalized forwarding**:==
With generalized forwarding, the match can be made over multiple header fields associated with different protocols at different layers in the protocol stack, and the action can include forwarding the packet to one or more output ports, load-balancing packets across multiple outgoing interfaces, rewriting header values (as in NAT), purposefully blocking/dropping a packet (as in a firewall), sending a packet to a special server for further processing and action, and more.


* Forwarding rule is only based on destination address.