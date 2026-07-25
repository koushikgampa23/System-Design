# System-Design
This Repo contains system design

# Networking and communications
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

### Types of DNS
    Root Name servers: Top level servers handling .com,.org etc
    TLD Name servers: Specific to domains like .com, .net
    Autoritative Name servers: Stores domain specific records
    Recursive Resolvers: Handles queries on behalf of users, contacting multiple DNS servers if necessary.
    flow:
        user request -> Recursive server(ISP or public dns) -> Root Name Server(Top level servers for .com, .org etc) -> TLD(Handles .com, .net, etc) -> Authoritative Name server(Stores domain-specific records) -> Resolved ip address returned -> website loads in browser
    
    Note:
        Authoritative servers are source of truth it stores actual dns records and returns ip address that is associated with the domain.
    
### DNS caching and performance optimization
    Reduces latency, Reduces load on DNS servers
    caching occurs in Browser caching, OS cache(Windows DNS cache), Recursive Resolver cache(ISP level)

    TTL(Time to Live): Determines how long a cache record is valid

### Step by step how dns works
    User types a domain the browser
    Browser cache check (if the ip address is already known)
    Operating system cache check.
    Query to the local DNS server(ISP or configured dns server)
    not found, query goes to Root dns server.
    TLD server provides details of authoritative dns server details
    Authoritative DNS server returns ip address
    Response is cached and returned to user

### Importance of DNS in large scale system
    Ensuring High availibity:
        Load balancing using DNS
        Anycast DNS for faster global resolution
    DNS failover stratigies
        Primary and secondary dns servers
    Content Delivery Networks(CDN) & DNS
        How dns directs users to nearest CDN node for fast loading.
    DNS Security risks:
        DNS poisoning, cache poisoing and DDos attacks

## Client Server Model
    A computing model where client request services and servers provides them.
    Foundation of modern web, database and application architecture
    Components of model:
        Client: The user facing applicaiton that sends request
        Server: A system that processes request and return responses
        Network: The medium that facilities communication between client and server
    Basic Steps:
        Client sends a request
        request transmitted over the network
        Server serves and processes the request
        Server sends the response
        Client receives and procesess the response
    Types of communication:
        Request/Response Model(HTTP, Rest API)
        Persistant Connections(Websockets, FTP sessions)
    Sync vs async
        Synchronous Communication:
            Clients wait for a response before proceding
            Used in Rest APIs, traditional web apps
        Asychronous Communication:
            Client doesnot wait for the response, can perform other tasks
            Used in messaging apps, live updates and iot applications
    Stateless servers vs Stateful servers:
        Stateless:
            No memory of past interactions; each request is independent
            Example: Rest APIs, HTTP servers
            Benefits: Scalability, easy caching, load balancing
        Stateful:
            Maintain session information across the requests
            Example: websockets, multiplayer games, banking applications
            Benefits: Personalization, seamless user experience
        
        State introduces complexicity once a server holds user specific information, scaling becomes harder, failover becomes more chanllenging and the request often need to redirected to the same the server instance.
        This created additional infrastructure requirements around session management and state syncronization
        As systems grow architectures choose stateless servers when ever it is possible

## Forward Proxy vs Reverse Proxy
    A proxy is a intermeditate server between client and another server
    Proxies helps with security, caching, traffic control, anonmity
    Two main types: Forward and revers proxy
    Forward Proxy:
        Sits between a client and internet
        Clients connect to the forward proxy instead of directly accessing websites
        Can filter content, provide anonmity and cache requests
        Common usecases:
            By passing geo-restrictions
            Anonymous browsing(VPNs , TOR)
            Caching web pages for faster access
        It is a primarly a client side tool
        It gives client a layer of control, security, and optimization before reaches the internet
    Reverse Proxy:
        Sits between users and backend services(used by servers)
        Clients doesnot directly communicate with backend servers - requests go through reverse proxy
        Used of load balancing, caching, security and ssl termination
        Common use case:
            Load balancing across multiple servers
            caching contents to improve speed
            DDos protection and security
        Once you have multiple application servers, you need single entrypoint that acts intelligently route traffic, distribute load, cache responses, enforce security polices, and handle cross cutting concerns without pushing that complexity into every backend service
        They also commonly used to handle SSL termination, centralizing encryption and allowing  backend to focus on business logic rather than connection management

    Forward Proxy vs revers proxy
    Feature         Forwarard                               Reverse
    Position        Between client and internet             Between Users and backend
    Who uses it     Clients(users, browsers, apps)          Web server, application server
    purpose         anonmity, filtering, access control     security, load balancing, caching
    Example         VPN, Web proxy                          ngnix, cloudflare, ALB

## Load Balancing
    Load balancing is one of the most important bulding block of system desgin
    A single server becomes both capacity limit and also a reliability risk. if a machines slows downs every one is affected, growth turns a single server into a single point of failure. That is where load balancing comes to the picture
    Once we move from a single machine, we need a way to distribute traffic across multiple servers and make those servers appear to be the single system to the user
    It enables horizontal scaling, it improves reslience

    The scaling challenge
    The first instance when a server slows down is adding more cpu, more memory, move to a larger server and that works intially
    The traffic is rarely linear, as demand increases, resource consumption increses, eventually the server becomes the bottleneck.
    Request begain waiting for responses, failures becomes visibile
    Buying larger machines is expensive and returns diminshes and we are still relying on single piece of infrastructure
    This are the problems with vertical scaling
    
    Horizonatl scaling challenge
        Capacity grows by adding more servers
        workload can be shared across machines
        users should not choose servers manually
        Traffic needs a distributed mechanism
    Bottleneck is how do we efficiently distribute the traffic with the available resources

    Load balancer:
        A load balancing becomes the systems entrypoint
        Incoming requests are distributed across servers
        Traffic is no longer dependent on single server
        Applications can scale more efficiently
    Load balaning enables Reliable systems:
        Multiple servers provide redundency
        Failed servers can be bypassed
        Maintance becomes safer
        Avalibity and resilience improve.
## API Gateway
    As system grows the number of clients and backend services grows and connecting every client directly to every service quickly becomes difficult to secure, monitor and evolve

    An API endpoint solves this problem by introducing a single entry point between clients and backend echo system
    Instead of pushing through authentication, authorization, routing, rate limiting, caching and request transformation into every service, we centerlize them in one single place.
    The API Gateway becomes the fornt door of the system
    This becomes espically valuable in a micro services environment, where client may otherwise need to communicate with dozens of independent services
    The key idea is that backend can focus on business logic, while the gateway handles cross-cutting concerns
    That seperation improves maintainability, strengthens security, and provides a controlled layer through which an entire API landscape can evolve and scale.

    How API Gateways can work?
    An API Gateway acts a revers proxy between clients and backend services
    It receives API requests, process them, and fowards them to correct service
    Key functions include request transformation, authentication, rate limiting, and response handling

    Popular API Gateway implemenations
        Open Source solutions: Ngnix, KONG, Trafix
        Cloud based solutions: AWS API Gateway, Google apigee, Azure API management
    When to use API Gateway?
    Best suited:
        Microservices architecture
        Multi-client API
        APIs requiring security, rate limiting and monitoring
    Avoid:
        Simple monolitic apps with minimal api exposure
        Low-traffic, internal only services

## CDN(Content Delivery Networks)
    A CDN is a global distributed network of servers that work together to deliver content efficiently
    Why CDN exists:
        Reduces latency, Enhances content availbility, Improves load handling, Security
    
    As traffic grows, the original server becomes both a scalability, bottleneck and a reliability risk.
    A CDN acts a distributed system in front of the system, absorbing traffic spikes, serving cached content at scale, and reducing load on backend infrastructure.
    It also improves reslience by rerouting requests when individual nodes or regions experience any issues.
    Modern CDN evolved from simple caching, Now they play critical role in security by filtering malicious traffic, mitigating DDos attacks, terminating TLS connections and protecting origin servers from direct exposure.
    In large scale systems, CDN is the first architectural layer users can interact with, making it key component for performance, avalibilty, scalability and security.

    why CDNs needed?
        The problems without CDN:
            High latency due to geographic distance
            Overloaded origin servers
            Bandwidth constraints and slow load times
    
    CDN Architecture:
        Origin server: Store the original content
        Edge server(PoPs): Stores cached content closer to users
        Request Routing System: Directs users to nearest PoP
    
    The goal of CDN is not to replace the origin, but reduce how often users need to reach it directly and to archieve that CDNs deploy edge servers, or Point of Presence(PoPs) across different geographical regions.
    This edge locations cache content closer to user, allowing requests to be served from a nearby location instead of travelling all the way back to origin.
    This is where most of the latency reduction comes from
    When a user sends a request, the CDN must decide which edge location should handle it.
    This decision is not only based on geographical location, It also considers factors like network conditions, latency, avalibility and server load to find best possible path

    How CDN works?
        1.User requests content
        2.CDN directs the request to nearest edge server based on geographic locaiton, network latency and server load
        3.Cache Hit: if the content is available in the edge server, it is delivered instantly
        4.Cahce Miss: if the content is not cached, the request forwarded to the origin server, fetched, and stored at the edge server for future use
    
    How CDN improves Performance, Reliability and security
    Caching and Replication(Reduces latency)
        Popular content is cached at edge locations worldwide
        Cache TTL and invalidation stategies maintain content freshness
        Reduces origin load and accelerates content delivery
    Load balancing and inteligent Routing(Improved availabilty)
        Traffic is distibuted across the multiple PoPs
        Geo-based, latency based, load aware routing selecting the best edge location
        Automatic failover reroutes traffic during outages
    Compression and Content Optimization(lower bandwidth costs)
        Gzip compression reduces payload size
        Image optimization (WebP, AVIF) improves delivery efficiency
        CSS/JS minification reduces download times
    Security and edge protection
        DDos mitigation through rate limiting and traffic filtering
        SSL/TLS termination secures communication
        Protects origin server from direct exposure
    
    Static vs dynamic content Delivery
        Static content: Images, Videos, HTML files
        Dynamic Content: API response, personalized pages
    
    API acceleration and edge computing(CDN for API's)
        Reduce api response times
        Edge caching for frequently accessed endpoints