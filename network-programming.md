Network programming
===================

IPv4 addresses can be mapped to IPv6 addresses by prefixing the four bytes in the IPv4 address with ::ffff. For example, 1.2.3.4 becomes :ffff:1.2.3.4.

Loopback addresses
------------------

 * IPv4: 127.0.0.1
 * IPv6: ::1

Link-local addresses
--------------------

These addresses can only be used for communicating between hosts on the same network, routers will not forward packets with these addresses as their destination.

 * IPv4: 169.254.x.x
 * IPv6: Any address starting FE80, FE90, FEA0 or FEB0.

Private use addresses
---------------------

Three ranges of addresses are reserved in IPv4 for private internal use:

 * 192.168.x.x
 * 172.16-31.x.x
 * 10.x.x.x

Generally speaking, the host with the private address must initiate communications in order to talk to the outside world.

Multicast addresses
-------------------

Multicast addresses potentially refer to an arbitrary number of destinations.

 * IPv4: 224-239.x.x.x
 * IPv6: Any address starting FF.

Multicasting is an advanced subject and tends only to be used in large networks - especially for delivery of multimedia content.

Port numbers
------------

Port numbers are the same for IPv4 and IPv6 and are represented by a 16 bit unsigned integer, giving a range of 1-65,535 (0 being reserved). Binding to a port below 1024 requires superuser/root privileges, although it is possible for a process to bind as root and then release these privileges and continue running as a different user.

The Internet Assigned Number Authority (IANA) oversees the assignment of well-known port numbers to certain applications and services. For example, port 80 is the standard port for running a HTTP server (and port 443 for HTTP over TLS).

The port number registry can be found online:

http://www.iana.org/assignments/port-numbers

Sockets
-------

There are two main types of sockets within TCP/IP:

 * Stream sockets: Use TCP as the end-to-end protocol.
 * Datagram sockets: Use UDP as the protocol.

Basic TCP client
----------------

The four basic steps for a TCP client to communicate are:

 # Create a TCP socket using `socket()`.
 # Connect to the server using `connect()`.
 # Send/receive data using `send()` and `recv()`.
 # Close the connection using `close()`.


 
