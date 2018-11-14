##  Step by step installation and settings Apache JMeter
### Installing Java
The installation of JMeter on Ubuntu requires prior installation of JAVA.  
 
### Installing Apache JMeter.
This short tutorial explains how to use multiple systems to perform stress testing. Before we start, there are a couple of things to check.

* the firewalls on the systems are turned off or correct ports are opened.
* all the clients and servers are on the same subnet.
* the server is in the same subnet, if 192.x.x.x or 10.x.x.x IP addresses are used. If the server doesn't use 192.xx or 10.xx IP address, there shouldn't be any problems.
* Make sure JMeter can access the server.
* Make sure you use the same version of JMeter and Java on all the systems. Mixing versions will not work correctly

After ensuring the presence of Java in your system, download the latest stable version of Apache JMeter from Apache JMeter download page. 

`wget http://redrockdigimark.com/apachemirror//jmeter/binaries/apache-jmeter-3.3.tgz`

Now, use the following command to extract the downloaded JMeter file. 

`tar -xf apache-jmeter-3.3.tgz`

Once it is downloaded, change its directory to apache-jmeter-3.3 > bin

`cd apache-jmeter-3.3/bin/`

## Jmeter Client instructions

**Settings before running**
1. Open jmeter.properties file in a text editor
2. Edit the line “#remote_hosts=127.0.0.1”
3. Add the IP address. For example, if I have jmeter server running on 192.168.0.10, 11, 12 and 13 the entry would like like this: remote_hosts=192.168.0.10,192.168.0.11,192.168.0.12,192.168.0.13

**Running Jmeter(client side)**

Go to jmeter/bin directory and run:

`./jmeter -Djava.rmi.server.hostname={client's IP}`

For example, if client machine have 10.20.10.104 IP, for running jmeter you should follow this:

`./jmeter -Djava.rmi.server.hostname=10.20.10.104`


## Jmeter Server instructions

**Settings before running**
1. Open jmeter.server file in a text editor
2. Add 

`RMI_HOST_DEF=-Djava.rmi.server.hostname={server's IP}`

after line:

`#RMI_HOST_DEF=-Djava.rmi.server.hostname=xxx.xxx.xxx.xxx`

For example, if server have 10.20.10.80 IP, you should use this:

`RMI_HOST_DEF=-Djava.rmi.server.hostname=10.20.10.80`

**Running Jmeter(server side)**

Go to jmeter/bin directory and run:

`./jmeter-server `

## Using file for test

To load test, you can use file(csv format).

**The same file should be in jmeter-3.3/bin directory on client and server machines.**

On Jmeter UI setting (client side), path to file as view follow:

Filename:testForLoad.csv



**Sources:**
1. https://stackoverflow.com/questions/14160241/jmeter-remote-run-and-csv-files
2. https://www.linuxhelp.com/how-to-install-apache-jmeter-in-ubuntu-16-04/
3. http://jmeter.apache.org/usermanual/jmeter_distributed_testing_step_by_step.pdf