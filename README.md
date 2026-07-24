# System-Design
This Repo contains system design

## Definations
### System design
    System design is the blueprint of a software system
    Define system architecture, components, interfaces and data flow
    Focus on scalability, reliability, performance and maintainabilty
    Establishes boundaries between services, databases and servers
    Converts business requirements into technical requirements
    Balanaces functionality with operational realities

    A good system is not focused on functionality alone, it must also scalable, perfomable and maintainable.

### Why is system design important
    Scalability and reliability - Ensures system handles millions of users without failure.
    Architectural thinking - Goes beyound coding, involves tradeoffs like CAP theorem, SQL VS NOSQL
    Career Growth - Essential for becoming senior engineer or architect
    Real world Problem solving - Helps in builiding actual systems, not just clearing of interviews.
    Trade offs and Decision making - Balances scalability, cost, speed and complexity
    Future Proofing - Prevents bottlenecks and allows smooth evolution of software

## Introduction to networking
    How request, data and services intaract with large scale applications

    Networking is the foundation of system design, every request, every database call, every user interaction ultimatly depends on how efficiently systems communicate with each other.
    As architecutural becomes larger and more distributed, network decisions influencing nearly every quality attribute like scalibity, performance, reliability, availablity and security 
#### Why networking matters in system design?
    Every system depends on data exchange between components
    Networking enables scalability, reliability and performance
    Key areas where networking plays a major role:
        Communication: Ensuring smooth data transfer between clients, servers and databases
        Load balancing: Distributing traffic evenly to prevent overload of a single server
        Security: Protecting data from unauthorized access and cyber threats
        Efficiency: Optimizing network performance to reduce latency and improve user experience
#### How networking impacts large scale systems?
    Helps handles millions of users concurrently
    Enables fast and efficient data exchange
    Reduces latency and improves system resilience
    Essential for cloud computing and distributed systems

## IP address
    Fundamental identity of every device
    IP(Internet Protocal) addresses are unique numerical labels assigned to each device on a network
    They enable communication between different machines, servers and services
    Two primary versions: IPv4, IPv6
    Two primary categories: Private, Public
### What is IPv4?
    IPv4(Internet Protocal Version 4) is the most commonly used addressing system.
    32-bit address format(eg: 192.168.1.1)
    Total address available are 4.3 billion
    Uses: Most traditional devices, webservers and most current internet devices
    Challenges: Limited IPs, fragmentation, security concerns
### What is IPv6?
    IPv6(Internet Protocal Version 6) is the next generation ip address.
    128-addressing bitformat - 2001:0db8:55a3:0000:0000:8a2e:0370:7334
    Total Address available: 340 undecilion (virtually unlimited)
    Designed for: IOT devices, mobile networks and future scalability
    Key benefits: larger address space, better security and improved routing efficiency
    Contains x:x:x : x : x:x:x:x
         site prefix  subnet(id)  Interface id
### Difference between IPv4 and IPv6?
                        IPv4                     IPv6
    Address Size     32bit                  128bit
    Address formate  Decimal(192.168.1.1)   Hexacode(2001:0db8:55a3:0000:0000:8a2e:0370:7334)
    Address space    4.3 billion            Virtually unlimited
    Security         Relis on additional     Built in security(IPsec)
                        protocals
    Performance      Limited due to NAT &   More efficient routing and handling
                        Fragmentation   
    Adoption         Still widely used       Slowly being adopted
### Public vs Private IP address
    Public IP's:
        Assigned by ISP's(Internet service providers)
        Used to communicate over the internet
        Unique worldwide
        Example: 192.203.23.45
    Private IP's:
        Used within local networks(LANs, Enterprises, homes).
        Cannot be accessed directly from internet.
        Examples:
            10.0.0.0 - 10.255.255.255
            172.16.0.0 - 172.31.255.255
            192.168.0.0 - 192.168.255.255
### Why do we need Private IP's?
    Conserves public IP address(IPv4 limitation)
    Enhances security(private ips are not routable across internet)
    Enables Network Address Translation(NAT) to allow multiple devices to share a single public IP.
    Common in corporate networks, data centers and cloud environments.
### The role of IP address in System design?
    Scalability: helps in designing distributed, multi region, and cloud based architecutes
    Security: Enables firewall rules, VPNs, and private networking
    Load Balancing: Uses IP based traffic distribution(eg: Round Robin DNS, Anycast IPs)
    Cloud Networking: Public, Private, and hybrid cloud IP management(AWS, GCP, Azure)
    Microservices and containers: Use Internal private IPs for communication
## DNS
    The phonebook of internet
    Translates human readable domain names into ip addressess
    Enables accessibility of websites
    Supports distributed, scalable internet architecuture.

    DNS provides a stable layer of abstraction, allowing users to keep using the same domain name while the underlaying infrastructure behind it evolves

    
        
