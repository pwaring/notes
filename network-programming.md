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



