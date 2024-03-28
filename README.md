# Self_Notes

# Simulating the Infra for Infinispan Cache cluster Cross-Site Replication: 

  Q. How to identify two IPs are in same network or in different ??

  Port: A port is a communication endpoint. Within an operating system, a port is opened or closed to data packets for specific processes or network services.

** Port numbers 0 to 1023 : well-known port numbers & are reserved for the most commonly used services.
** Port numbers above 1024 are referred to as ephemeral ports.
     Port numbers 1024 to 49151 are called the registered/user ports.
     Port numbers 49152 to 65535 are called the dynamic/private ports.
     
TCP and UDP, which are the most common protocols for packet transmission in the network layer.

  1. Open a Port on a machine:
  https://www.digitalocean.com/community/tutorials/opening-a-port-on-linux



# Creating Infinispan server using configuration: 

Machine 1
podman run -d --name infinispan-site-1 -e USER=keen -e PASS=KeenAble@123 --net=host --user=root -v /home/rocky/server1:/opt/infinispan/server1 -v /home/rocky/newxsite.xml:/opt/infinispan/server/conf/newxsite.xml -p 11222:11222 -p 7900:7900 quay.io/infinispan/server:15.0 -c newxsite.xml -s server1 -Dinfinispan.site.name=site1

Machine 2:
podman run -d --name infinispan-site-2 -e USER=keen -e PASS=KeenAble@123 --net=host --user=root -v /home/azureuser/server2:/opt/infinispan/server2 -v /home/azureuser/newxsite.xml:/opt/infinispan/server/conf/newxsite.xml -p 11222:11222 -p 7900:7900 quay.io/infinispan/server:15.0 -c newxsite.xml -s server2 -Dinfinispan.site.name=site2

