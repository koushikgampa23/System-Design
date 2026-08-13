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

## Protocals
    TCP and UDP:
        TCP(Transmission Controlled Protocal):
            Connection oriented protocal
            Reliable, ordered and error checked communications
            Ensures data reaches the destination correctly
        
            TCP uses three way handshake 
            This setup introduces small amount of latency, but it creates foundation of reliable communication
            It doesnot just data it tracks it too, every segment is numbered, acknowledgments are exchanged and missing data is automatically retried.
            Even if the packets choose different network paths, when it arrives in wrong order, TCP reassembles them in the correct order before passing to application
            This reliabilty is essential for workloads where correctness matters over raw speed
            TCP gurantees what was sent is what was arrived
            The tradeoff is additional overhead, connection establishment, acknowledgement, retransmission and ordering, all this things consumes times and resources.
            
            Example: Transfering money, downloading files
        
        UDP(User Datagram protocol):
            Connection less protocal
            Faster but no delivery gurantees
            No retransmission of lost packets

            It is designed to 
            Instead of maximazing reliability, it minimizes communcation overhead and latency
            It assumes getting data more quickly more important than guranted data
            There is no handshake, no ongoing tracking of data
            An application can simply send packets and move on this makes the udp lightweight and efficient

            Example: video calls, online games
        
### TCP Vs UDP
    Feature                 TCP                                                             UDP
    Reliability         Reliable(ensures data security)                                     Unreliable(no gurante of delivery)
    Speed               Slower(due to error checking and retransmission)                    Faster(no retransmission overhead)
    Connection type     Connection-oriented(establishes connection before communication)    Connectionless(sends data without setup)
    ordering            Ensures packets arrive in order                                     No gurantee of packet order
    Error handling      Built in error checking and retransmission                          Minimal error checking, no retransmission
    Overhead            High(due to handshake, sequencing, and acknowledgments)             Low(minimal protocal overhead)
    Use cases           File transfer, Database communication,web browsing                  Video streaming(Youtube, netflix, zoom)

### HTTP protocal
    It is the backbone of the web
    HTTP - HyperText Transfer Protocal
    The foundation of web application
    Defines rules for requesting and tranfering resources(eg: webpages, API, images)
    Works over TCP/IP(Port 80 for HTTP, Port 443 for HTTPS)

    Key features:
        HTTP is stateless each request arrives independently with no built in memory 
        Text based protocal (easy to read and debug)
        Supports multiple methods(GET, POST, etc..)
    
    Components of HTTP request:
        Method: Defines the action(GET, POST, etc.)
        URL: The resource being requested
        Headers: Metadata(eg: user-agent, content type)
        Body(optional): Data sent in POST/PUT requests
    Componenets of HTTP response:
        Status Code: Indicates success or failure (eg 200, 404 not found)
        Headers: Metadata about response
        Body(optional): The actual content returned
    Request/Reponse life cycle:
        The browser sends a request
        The webserver processes the request
        The server generates a response and sends it back
        The browser renders the response
    
    Stateless nature of http:
        Http doesnot retain memory of previous request
        Each request is treated as independent transcation
        Challenges of stateless:
            its hard to maintain user sessions
            Each request must carry all necessary information
        How do you handle state?
            cookies - small pieces of data stored in browser
            sessions - server side storage of user state
            Tokens - used for authentication and authorization
    HTTP methods:
        GET- Retrive a resourse
        POST- Create a resourse
        PUT- Update a exisiting resource
        PATCH- Partially update a resource
        DELETE- Delete a resource
    
    HTTPS:
        HTTPS is the secure version of HTTP, using SSL/TLS encryption
        It ensures data confidentiality, integrity and authentication
        Used for secure webites, online banking and e-commerce
        works on port 443 instead of 80

        HTTPS provides 3 essential guarentes:
            Confidentialty ensures that only the intended parties can read the data
            Integrity protects against tampering while data is in transit
            Authentication verfies that users can actually communicating with the legtimate website or API and not an attacker impersonating it

### Rest and RestFulnes - API Design Priciples
    Rest:
        Defination: REST(Respresentational State Transfer) is an architectural style for designing network applications
        Key idea: Uses standard HTTP method and stateless communication
    Why rest matters?
        Simpilicity and scalability: Based on standard HTTP
        Interoperability: Works across different platforms
        Efficiency: Uses caches, stateless for performance
    REST Constraints(Core Principles)
        Client server architecture
        Stateless
        Cacheability
        Layered System
        Uniform interface
    RESTful API Design priciples
        Resource Based approach
            Get /users/{id} to retrive a user
            Post /orders to create a new order
        Proper HTTP methods usages:
            GET- Retrive a resourse
            POST- Create a resourse
            PUT- Update a exisiting resource
            PATCH- Partially update a resource
            DELETE- Delete a resource
        Stateless Interactions
        Consistance in URL structure
            use plural nouns for collections: /users, /orders
            Avoid including actions in url: users/{id}/activate -> /users/{id} with PATCH
            Implement versioning for backend compactability: /v1/users    
        Resources and endpoints
            Resources: Entites like users, orders, products
            Endpoint Examples: Get /users/{id}, POST /orders, delete /users/{1}
        JSON vs XML in REST apis
            why json?
                lightweight
                Faster parsing
                Readable
            when to use xml?
                Legacy system
                Data validation needs
### Real time communication protocal
    Real time communication refers to the continous exchange of data with minimal latency.
    why realtime is important(instant chat, live stock updates)
    Challenges of tranditional request-response HTTP model.
    Alternatives to improve real time data exchange:
        pooling
        websockets
        Server sent events
        long pooling

    Websockets: Persistant full duplex communication
    Defination: Websockets provide a persistant, full duplex communication between client and server over a single tcp connection
    How they work?
        Websockets handshake using HTTP upgrade request
            Step1: Client request an upgrade to websockets
            Step2: Server accepts and keep open the request
        Connection remains open for continous data exchange
            Step3: Data is exchanged in realtime using frames
            Step4: Either party can close the connection when done
        This reduces latency and network overhead
    Advantages:
        persistant connection = lower latency
        Reduces overhead compared to http pooling
        Essential for real time applications
    
    HTTP requests are designed to retrive information, while websockets are optimized for continous conversation

### Long Pooling: Simulating realtime with HTTP
    A technique where a client send a request to the server and waits until the server has new data to respond
    How it differs from regular pooling
        Instead of immediate responses, the server holds the request until new data is available
    How long pooling works:
        a. client sends an http request
        b. server holds the request until the data available
        c. server responds with new data
        d. Client immediately sends another request

    Use websockets when:
        High frequency, bi directional data exchange is needed
        Low latency is critical
    Use long pooling when:
        Websockets are not supported or overkill
        Periodic updates are sufficient(notifications)
    Real world examples:
        Slack: Websockets for chat
        Twitter notificaiton: Long pooling for notifications
        IoT devices: Long Pooling for intermittent updates
### Modern APIs go beyond Rest(grPC, GraphQl)
    Limitations of restapi:
        Over fetching and underfetching
        High latency(Mulitple requests are needed to get complex data)
        Not optimized for realtime communcation(Pooling required)
    
    In rest server decides the shape of responses that often leads to over fetching where client gets more data than needed or underfetching where they need additional request to complete a screen
    Increase network overhead and reduce efficiency
    The problem becomes more visible in the modern application where the user needs more aggregated data from multiple resources

    Graph QL focus on flexible and precise data retrival, while grPC focus on hight performance communcation between services

    gRPC: A high performance, binary protocal optimized for microservices and realtime communication
    Graph QL: A flexible query language that allows clients to fetch only the data they need

    gRPC is gets permformace from the combination of design together, the foundation is http2, HTTP2 allows multiple requests and responses to share the same connection simultaneously.
    This eliminates much of a overhead and keeps communication fast even when services are interacting with each other on same time
    HTTP2 also enables efficient streaming, instead of client and server opening a new request, a client and server can maintain long lived connection and continously exchange data in both directions, This makes gRPC systems more efficient for real time systems, event systems, and service to service communcation where updates happen every frequently
    The second advantage is Rather than sending that verbose json document, gRPC uses protocol buffer(ProtoBuf) data is encoded in compact binary format that is smaller on network but faster on serailizing and deseralizing.
    The combination of HTTP2 and ProtoBuf for low latency and high thorughput

    gRPC uses and when to use:
        Microservices - Fast inter service communication
        Realtime streaming - Full duplex bi directional data transfer
        IoT and low bandwidth applications - Efficient binary communication
        Multi-language ecosystem - Auto generated client and server code
    Suited for live analytics, telemetry, collaborative applications, financial systems

    Graph QL:
        Instead of multiple REST endpoints, Graph QL has one endpoint where client specify the data they need
        Graph QL schema defines data types and relationship between data
        Clients sends query -> Graph ql server resolves fields dynamically
    
        No need to create seperate endpoints for mobiles and websites
        The frontend application decides what data it needs
        
        when to use?
            Frontend optimization: Clients fetch exactly what they need
            Reducing API Requests: One query replaces multiple REST calls
            Mobile and web apps: Handles slow network and multiple data sources
            Aggregating Data from multiple servers: Simplefiles fetching data from different databases and apis
        Graph QL can be used as an aggregation layer
        Behind one single graph QL endpoint, the server can pull data from multiple endpoints, multiple servers, multiple microservices or third party api to present a unified response to the client
        This shields the frontend teams from backend complexity and creates a cleaner integration model
        It is not primarly about performance it is about flexibility
        when client requirements vary significantly and data comes from multiple resources graphql simplies how application can communicate

## Architectural Patterns
    What is a software architecture?
        The structure of a system, including its components and relationships
    Architecture impacts scalability, performance and maintainability
    Importance of system design and Key design
        Scalability: Ability to handle increased data and traffic
        Maintainability: How easily the system can be updated or modified(evolved)
        Performance: Efficiency and responsiveness under load
### Software Architecture Patterns and styles
    what is a software architecture?
    Definition: The high level structure of software system, defining component, their relationships and the way they intract
    It impacts scalability, maintainability, performance and system behaviour.

    Explanation:
    Think of it has a blue print of the system, blueprint influences how a structure is built, expanded and maintained
    Software architecture influences how a system evolves over time.
    It establishes boundaries, communication patterns and overall organization of solution

    Common Architectural styles:
        Monolithic
        Layered(N-tier)
        Client server
        Microservices
        Event Driven
#### Monolitic Architecture
    Definition: A single unified system where all the components are tightly coupled and work as a single unit
    Pros:
        Simple to develop and deploy
        Easier to manange in smaller applications
    Cons:
        Hard to scale
        Difficult to maintain as code grows
        High risk of failure, A single bug can takedown an entire system
    Usecase:
        Small scale applications, startups, simple CRUD apps
    
    Application: UI - Business logic - data access layer -> database
    
    Explanation:
    Monolitic Architecture in fact many of the software applications begin with this architecture.
    Because simplicity is more valuable than architectural sophistication.
    In a monolitic architecture entire application is built and deployed in single unit, The user interface, database logic, data access layer, and supporting functionality all live within the same codebase and typically share the same deployment process.
    This makes development straight forward because everything stays in one place and developers can easily understand what parts of system interact.
    Biggest advantage is simplicity, it is easier to Develop, test, deploy and debug because there are no distributed communication concers, service discovery, mechanisms, or interservice dependencies to manage.
    Scaling becomes inefficient because even if only one module experiences heavy traffic, the entire applicaiton must be scaled
    Large codebases also becomes harder to understand, test and modify, increasing the overall risk that change in one area impacts other area.

#### Layered(N-tier) Architecture
    Definition: A system split into multiple layers(eg: presentation, Business Logic, data) to seperate concerns
    Pros:
        Clear seperation of concerns
        Easier to scale and maintain as compared to monolitic
    Cons:
        Performance overhead due to layers
        May result in tight coupling between certain layers
    Use cases: Enterprise applications, CRM Systems, Banking applications

    Application: User interface -> Business logic -> Data Access -> RDBMS

    Explanation:
        As application becomes layer mixing user interface code, business rule and database logic in the same space quickly becomes very difficult to manage.
        The solution was to seperate responsibility into distinct layers, each focused on a very specific concern.
        The presentation layer handles user interactions, the business layer contains the applications core rules and workflows and the data layer manages communcation with database and external storage 
        Each layer has a well defined responsibilty and communicates through controlled interfaces, creating a more organized and maintainable structure.
        The bigges advantage is seperation of concern, when responsibilities are clearly defined, teams can work more efficiently, code becomes eaiser to understand and changes can often made within one layer without impacting the entire application
        The request has to reach multiple layers before reaching the database and return through the same path, which can introduce additional latency.
        Overtime layers can also become tightly dependent on one another, make changes more difficut than architecure as intended.
        It is not primarly focused on scalability, it focused on managing the complexicity
#### Micronservices architecture
    Definition: A system built as a collection of small independent services, each focuses on a specific business capability
    Pros:
        Independent services can be scaled, deployed and developed seperatly
        Flexibilty in tech stack for each service
        Better fault tolerance
    Cons:
        Increased complexity in communcation and coordination
        Need for robust DevOps and automation pipelines.
    Use cases: large scale applications, e-commerce applications, modern cloud based systems

    Explanation:
        Instead of treating the entire application as a large unit, microservices organize the system around business domain
        An ecommerce application contains seperate services like product, inventory, orders, payments and notifications
        Each service can be developed, deployed, scaled and maintained independently, allowing teams to move faster without coordinating every change across the application.
        This independence is the advantage of the microservices, services can scale based on their individual work loads, teams can choose technologies that best fit their domain, failures can be often isolated rather than impacting entire application
        Mainly used in large scale applications, rapidly evolving products.
        Microservices replaces application complexity with distributed complexity, 
        What was once a function call now it will be a network call.
        Teams must deal with service discovery, network latency, retries, monitoring, distributed tracing and data consistancy across the multiple services now.
        Operation excellence becomes just as importanant as developing the application.
        That is why microservices are most successfull when supported by strong devops practises, automation, observability, and mature engineering teams
#### Event driven architecture
    Definition: A system where components communicate through events(messages) instead of direct calls, enabling loose coupling
    Pros:
        Highly decoupled architecture
        Excellent for handling asynchronous workflows
        Better scalabilty for high traffic systems
    Cons:
        Debugging and tracing becomes more complex
        Difficult to ensure data consistance across services
    use cases:
        Real time systems, IOT applications, financial trading platforms
#### Factors influncing Architecture Selection
    Business needs: What problems are we solving? what is the business goal?
    Scalability: How much traffic and data should sytem to handle?
    Performance: how fast should the system respond to users?
    Maintainability: How easy is to make updates, fix bugs, and evolve the system over time?
### Multi tier architecture
    Multi tier architecture is a software design pattern that structure the applications into multiple layers, each responsible for specific functions. This seperation enhances scalability, maintainability and security.
    Key points:
        Organizes applications into independent layers
        Seperate concerns: UI, business logic, and data storage
        Enables better scalability, performance and security
        Used in web applications, enterprise systems, and cloud architectures
    
    Explantion:
        the teams can modify business rules without redesigning the ui. databases can evolve without affecting application workflows, and individual layers can be scaled based on demand. It also improves security by controlling how data flows between layers, rather than exposing critical systems directly.

#### 2 Tier architecute
    Definition: The 2 tier architecture consists of Client layer and database layer, the client directly intracts with database, without an intermediate business logic layer.
    How it works:
        Client layer: User interface, application logic
        Database Layer: Stores and retrives data
        Data flows directly between client and database
    Pros:
        Simple to implement
        Fast for small scale applications
    Cons:
        Poor scalability(limited to few users)
        Security risk(direct database access)
    Example use case:
        A desktop application directly quering an sql database
    
    Architecture: Presentaion layer - data layer -> database

#### 3 Tier architecture
    Definition: 3 tier architecture introduces middle layer (business logic layer) between the UI and database
    How it works?
        The frontend interacts with business logic layer(API server)
        The business logic layer processes the request and interacts with database
    Pros:
        improves scalability and security
        Better seperation of concerns
        Easier maintenance
    Cons:
        Slightly higher latency due to extra processing
    Example:
        Traditional web applications

    Architecture: Presentational layer -> business logic layer -> data access layer queries -> database

#### N Tier architecture
    Definition: N tier architecture goes beyond 3-tier architecture by adding more specific layers like caching, API gateway, microservices etc.
    why use N-tier:
        Handles high traffic and complex business logic
        Allows independent scaling of different services
    Examples:
        Microservices-based applications
        Large scale enterprise software
    
    Architecture: users -(requests)-> Frontend -(traffic distribution)-> load balancer -(API requests)-> API Gateway -(Routes Requests)-> Microservices layer

    More layers means more infrasturcture, more monitoring, more deployment pipelines and more points of failures to manage

    2-Tier is simple but limited
    3-Tier is the standard for web apps
    N-Tier is for large-scale, cloud native systems

### Microservices Architecture
    Definition: Microservices Architecture is a software design pattern where applications are structured as a collection of small, loosely coupled services, each resposible for specific function.
    Characteristics:
        Independently deployable services
        Loosly coupled and modular
        Scalable and fault tolerant
    How to identity microservice?
        Business Capability: Each service should align with a specific business function(Payments, orders, etc)
        Single Responsibility Principle: A microservice should do one thing well
        Data ownership: Each microservice owns its own database - avoid shared databases
        Independently Deployable: Should be deployable and scalable without effecting others
    How to structure microservices:
        Decompose by business domain: Use Domain-Driven Design(DDD) to group services logically.
        Define clear APIs: Services should communicate via well defined apis(REST APis, gRPC, or events)
        Choose the right granularity: Avoid making microservices too large(monolith in-disguise) or too small (high complexicity)

#### Communication in microservices
    Synchronous Communication:
        Rest APIs(simple, highly used but has high latency)
        gRPC (Efficient, binary format, better performance)
    Asyschronous Communication:
        Event Driven messaging(Kafka, RabbitMQ, SNS/SQS)

    If we use rest api every network call adds latency, as services grow response time can increase across the entire request chain.
    Many orgs use gRPC for service to service communication, since it uses protobuffer and a compact binary fomat, it reduces payload size and delivers lower latency and higher throughput than traditional REST APIs
    This makes it effective for internal microservices communication, where performance matters a lot.
    In the asyschoronous communication:
        A service publishes a event and any interested service can react independently, this creates much looser coupling and allows system to scale much more effectivelty,
    
    Sychronous communication is ideal when we need immediate reponse, while event driven excel when scalability, resilience, and loose coupling  are our primary goals.

#### Challenges of microservices
    Data consistancy: Distibuted databases -> Eventual consistency
    Distributed tracing: Difficult to debug and track requests
    Network overhead: More API calls -> increased latency
    Security: Authentication, authorization and data protection

    In a monolith a single database transcation can keep everything syncronozied.
    In micro service architecture, each service owns its own database which means mainting consistency across the application services requires eventual consistency.
    
    For example: when order is placed, updates to inventory, payment, and shipping may occur asyncronously rather than instant, the system remains correct, but consistancy is archieved over time rather than in a single transcation.

    Challenge in debuging and tracking
    when a user sends a request it travels through 5-6 microservices before getting response, when something goes wrong identifiying where the failure occured can be difficult
    That is why distributed tracking tools such as OpenTelemetry and Zipkin have become essential

    Network over is another challenge
    Techiques such as gRPC, caching, request aggregation and asynchronous communication help to reduce overhead.

    Security:
    In monoliths the security is centerlized the authentication, authorization, data encryption, secure connection to sensitive data are handled centerally.
    In the microservices each serive needs to handle it.
    Technologies like API Gateway, OAuth, JWTs, mutual TLS and service mesh is commonly used across the systems

    Microservices solve scalability and organizational challenges, but they also introduce distributed system challenges that architects must deliberately design from day one only.

#### Scaling strategies in microservices
    Horizontal Scaling: Add more instances of a service
    Auto scaling: Scale up/down automatically
    Sharding and Database scaling: Split databases for high traffic services

    Instead of making server more larger and more powerful, we create additional instance of service and distribute traffic across them using load balancer. 
    For example during a major sale the order service may experience a surge in requests, while other services remain ideally stable.
    we can scale only the order service instead of entire applicaiton. As system grows, manuall scaling becomes impossible, autoscaling becomes more valuable
    
    Platforms like kubernetes can automatically add or remove service instance based on metrics like CPU utlization, memory consumption, or request volume.

    This ensures that the system can handle traffic spikes while avoiding unnecessary infrastructure costs while system is quite

    In large applicaiton the database becomes the bottleneck. To address this architectes use database scaling techniques such as read replicas and sharding.
    Read-replicas distribute read heavy workloads across database instances, while sharding partition data into smaller segments based on customer ID, tenant id or geographical region.

    The architecural lesson is that true scalability requires thinking beyond applicaiton servers.A scalable microservice platform combines service level scaling, automated elasticity and database optimizations to ensure that the entire systems can continue to grow without sacrificing performance or availability

#### Real world example
    Netflix: Uses microservices for video streaming and personalizaiton
    Uber: Scales ride-matching, payments and navigation independently
    Amazon: Each service(search, payments, recommendations ) runs separatly

#### Summary
    Microservices = Scalability, Fault Tolerance, Faster development
    Required API gateways, Service Discovery, Load balancing
    Challenges: Data consistancy, debugging, deployment complexity

### Event Driven Architecture
    Definition: A system design where components communicate through events rather than direct calls.
    Key characteristics:
        Asynchronous processing
        Loose coupling
        Scalability and flexibility
    why use it?
        Enhances system responsiveness
        Enables realtime event processing
        Supports complex workflows
    
    Event Driven communication emerged since service to service communcation directly became bottleneck as system grow. when every component depends on another component responding immediatly, scalability, resilence and flexibity become harder to archieve

    Instead Event driven architecture allows components to communicate through events, signals that something happened, without needing to know who will react to signals.

    A key characterists of this approach is asyncronous processing rather than waiting for response, the service can publish a event and continue its work when the other components processes that event independently.
    This reduces waiting response time and improves overall system responsiveness.
    Another major advantage is loose coupling, the producer and consumers of events are seperated each other, which means teams can modifiy, deploy or scale the service independently without creating tight dependency across the system
    
    New consumers can subscribe to existing events without modifiying the original service, making it to extend business workflows overtime.

    It is very common in realtime notification, financial transcations, order processing, IoT platforms, and systems where multiple components has to react for events

    The key takeaway is that event driven architecture systems are designed to be responsive, scalable, and adaptable making them a powerful architecture style for modern distributed systems

    Synchronous vs Asychronous Systems
    Synchronous Communication(Request-Response Model)
        Blocking calls
        Tight coupling
        Example: Traditional HTTP APIs
    Asychronous Communication(Event Driven model)
        Non blocking
        Decoupled components
        Example: Message Queues and event brokers

    Pub-Sub vs Event Streaming
        Publish-Subscribe Model(Pub-Sub):
            Events are broad casted for multiple subscribers
            Each subscribers get the event once
            Example: RabbitMQ, AWS SNS
        Event Streaming:
            Events are stored and consumed in order
            Consumers process events at different times
            Example: Kafka, AWS kinesis

    In pub/sub a publisher broadcasts an event and all interested subscribes receives the event. The publisher doesnot know how the subscribers are, and consumers dont need to know anything about publisher. This makes the system highly decouples and fan out scenarios such as notification, alerts or triggering downstream workloads.
    Once an event is triggered it is typically not retained for long term replay, so subscribers are expected to process when the event arrives

    Event streaming takes the idea one step further
    Instead of treating events are transit messages, events here are stored in an ordered, durable log.
    Consumers can read events whenever they choose, replay historical events or even process the same event stream mulitiple times for different purposes
    This capability is extermely valuable for analytics, auditing, monitoring, data pipelines and large scale system where event history is valuable asset.

    pub/sub vs event streaming
    Pub sub focuses on distributing events to interested consumers in realtime,
    whereas event streaming treats events as a permanent source of truth that can be consumed, replayed and analyzed long after the they were original generated.
    Choosing between them depends on wheather you only care about delievering events now or wheather you also need to preserve and process event history over time.

#### Key components of event driven systems
    Event producers(Generate Events)
    Event Brokers(Transit and store events) - Example: Kafka, Rabbit MQ, AWS EventBridge
    Event Consumers(React to events)
    Event Storage(Log-based persistance for replaying events)

#### Challenges in Event Driven Architecture
    Eventual consistancy(No immediate data synchronoizaition)
    Ordering Gurantees(Ensuring events are processed in sequence)
    Fault Tolerance and Retires(Handling failures gracefully)
    Debugging complexity(Tracking events across microservices)

    Because services communicate asyncronously data updates dont become visible everywhere at the same moment
    An event may be published immediately, but downstream systems process it some seconds later.
    This temporary inconsistancy is acceptable, but requires architects to think differently than they would in a traditional transcation system
    Techniques such as idempotant consumers, compensating actions and carefully designed business workflows are commonly used to manage this reality.
    Another challenge is maintaining ordering. In distributed systems event can arrive out of sequence or be processed concurrently by mulitple consumers.
    
    Imagine processing payment completed event before the corresponding order created event.Without proper control the system may reach the invalid state, This is why platforms such as kafka provide partition based ordering gurantees and why systems use sequence numbers or versioning strategies  
    
#### Best practises
    Use idempotent event processing to avoid duplicates
    Implement dead letter queues for failed messages
    Choose right event broker based on system needs
    Ensure event versioning to handle schema changes

    In distibuted system duplicate event delivery is not a bug. it is a expected reality, Retries, network interpution, and broker failure can all cause the same event to be delivered more than once.
    Consumers there for be designed so that processing an event multiple times produces the same outcome as processing the event once
    This prevents such as duplicate payments, duplicate orders or repeated notifications.

    Implement dead letter queues
    Not every failure can be resolved using retries.
    Some messages may be malformed, contain invalid data or repeatedly fail business validation, rahter than blocking entire processing pipelines, failed events should be isolated and moved to a dead letter queue, where they can be inspected, analyzed, and handled seperatly
    This significantly improves system realiability and operational visibility.

    Choosing right event broker
    kafka excels at high throughput event streaming and long term rentension
    RabbitMQ is often preferred for traditional message queuing patterns
    AWS Eventbridge simplify cloud native event routing

    without the versioning startegy a simple schema change can break downstream services.
    Therefore designing events with backend compactabilities in mind ensures that producers and consumers can evolve independently without disrupting the entire system

#### Use cases of event driven architecture
    Logging and auditing(Track changes over time)
    Real time notification(Chat apps, stock price updates)
    Microservices Decoupling(Independent scalability, and fault tolerance)
    IoT Systems(Senor data processing)
    E-commerce Order Processing(Order placed -> Payment processed -> inventory updated)

#### Summary
    Multi-Tier architecture: layered approach for scalability and seperation of concerns
    Micronservices architecture: Decoupled services enabling independent scaling and deployment
    Event driven architecture: Asyncronous, scalable, and loosely coupled systems.

## Web concepts in system design
### Why websessions matter?
    Web applications often need to track user state(eg: login status, shopping cart, user preferences)
    HTTP is stateless, meaning each request is independent
    Goal: Understand how to maintain state in web application
    It provides a way to pass mulitple requests with the same user and maintain context across
    
    Technologies such as cookies, server-side sessions, and authentication tokens enable applications to track user state, while balancing security, scalability, and user experience

    Http:
        HTTP doesnot retain memory of previous requests
        Each request must contain all necessary information

    Techniques for Maintaning state:
        Session Based Authentication(Server side session storage + Cookie for session IDs):
            The server maintains session state
            The client holds only the session id (usually in cookie)
        Token based authentication(JWT, OAuth Tokens)
            The session state is embeded within the token itself
            The server doesnot need to track user sessions
    
    In session based authentication:
        The server owns the user state, the server creates a session record and returns the session identifier to the client.This is typically stored in a cookie at client side.
        Onsubsequent requests the server sends the session id and server uses that session id to retrive user data.
        This model is straight forward and secure.
        As system grows, managing, syncronizing session data across multiple servers can become an operational challenge.
    Token based authentication:
        Instead of storing session information on server, the necessary user context is embedded inside a signed token, such as JWT token, and each request carries that token and server validates without looking up any session state on server side.
        This makes the architecture naturally stateless and easier to scale across distributed systems and microservices.

    Session based authentication offers great control over user session while 
    Token based authentication simplifies the horizontal scaling.

    In session based authentication:
        when a user logs in, the server creates a session record containing information such as users identity, permission, and other relevent state. The server then generates a unique session id and sends it back to client, typically through a cookie.
        from that point on ward, every request automatically includes this session id cookie,The server uses this identifier to locate the corresponding session data and determine who the user is, without requiring them to authenticate again.
        It works very well in traditional web applications because it gives the server complete control of the session management.
        Techiniques such as sticky sessions, session replication, or centralized session store like redis.
    In token based authentication:
        Instead of storing session information, the user information is packaged into the self contained token that travels through each request.
        When a user authenticates, the server generates a token commonly a JWT, that contians information such as user's identity, roles and permissions, the client stores this token and sends it back with sequent requests, typically in authorization headers.
        Rather than looking at session, the server validates the token and extracts the information that it needs.
        The biggest advantage of this model is scalability. Since the server doesnot maintain the session state, any instance in a distributed system can process the request without relying on shared session storage.
        This makes it particularly attractive for apis, microservices, mobile applications and cloud native architecture.
        It has challenges such as token expiration, revocation and security becomes more challenging than simply deleting a server side session.
        As a result, token security, expiration policy, and proper validation becomes critical part of overall authentication.

#### Security Concerns in Session Management
    Session Hijacking: Stolen session IDs
    Cross Site Request Forgery(CSRF): Unauthorized actions
    Secure cookie Handling: Avoiding theft via secure, HTTPOnly, and Same site flags

    If a attacker can compromise a users session, they can often bypass the entire authentication and act as that user, One of the most common threat is session hijacking, where a user obtains a valid session id and uses it to impersonate the real user.
    This can happen through network interception on unsecured connections or client side vulnerability like XSS.
    To reduce this risk modern applications enforce HTTPS, rotate session identifiers after authentication, and limit session life times.
    The another very major concer is cross site request forgery, or CSRF.
    A malicious site tricks a user's browser into sending authenticated requests to another application where user is already logged in. Because the browser includes session cookies, the request may appear legitimate. But this are not legitimate requests.
    Defenses such as CSRF tokens, same site cookies and additional verfication for sensitive action help to prevent these attacks

#### Best practises for scaling session management
    Sticky sessions vs Distributed session
    Storing session data in redis, Memcached
    Stateless authentication(JWTs) for scalability

    Sticky sessions a load balancer always ensures that a users request is always sent to the same server, while it is simple to implement that creates uneven load and impact availability if the server becomes unhealthy.
    A more scalable design is distributed session management.
    Instead of storing sessions locally in application servers, sessions data is placed in shared storage where all the servers can access this allows request to be routed to any available instance improving scalability and fault tolerance.
    
    Tech such as redis and mem cached is most commonly used
        They are inmemory data stores,They provide extermly fast lookups while enabling session sharing across the entire server fleet.
        In large scale systems redis is often prefered since it offers persistance, replication, and high availability.
    
    For maximum scalability, many modern architecutures move towards stateless authentication using JWTs since authentication data is carried within the token itself application server no longer need to perform session lookups
    This reduces infrastructure dependencies, and works perfectly well in microservices, cloud native platforms and api driven systems

### How CSRF validation implemented in django
    CSRF attack?
        CSRF (Cross-Site Request Forgery) is an attack where an attacker tricks a user's browser into sending an authenticated request to a trusted website where the user is already logged in. The attack works because the browser automatically includes the user's authentication cookies with the request.

    1.user logins the server generates session id, csrf token(random string) and sets cookie in browser
        HTTP/1.1 200 OK
        Set-Cookie: sessionid=abc123; HttpOnly; Secure
        Set-Cookie: csrftoken=XYZ789; Secure
    2.Frontend sends request to backend
        const response = await axios.post(
            "/api/transfer",
            {
                // your request body
                // ...
            },
            {
                withCredentials: true, // equivalent to credentials: "include"
                headers: {
                "X-CSRFToken": Cookies.get("csrftoken"),
                },
            }
        );
        Note:
            1.browser automatically sends cookie
            2.React explicity sends X-CSRFToken in headers
    3.Django recives the request
        Django checks the session id is valid or not from session table
        CSRF middleware checks
        Cookie token == Header token (or)
        Cookie token == Form token
        valid:
            Request accepted
        Invalid:
            403 forbidden
    4.Is the CSRF token stored in the database?
        by default No
        If CSRF_USE_SESSIONS = True is configured, Django stores the CSRF secret inside the user's session instead of in a cookie. It still does not create a separate CSRF table.
    
    Scenario: How Django CSRF Protection Prevents Cross-Site Request Forgery
    - A user is logged into andhrabank.com and has valid cookies (sessionid and csrftoken) stored in their browser.
    - The user then visits evil.com.
    - evil.com can attempt to make the browser send a request to andhrabank.com (a Cross-Site Request Forgery attack).
    - Depending on the cookie's SameSite setting, the browser may automatically include the cookies (sessionid and possibly csrftoken) in that request.
    - However, evil.com cannot read the cookies belonging to andhrabank.com because of the browser's Same Origin Policy.
    - In a React + Django application, React reads the csrftoken cookie and sends its value in the custom X-CSRFToken header.
    - evil.com cannot send the correct X-CSRFToken header because it does not know the CSRF token value. It cannot read the cookie or access the React application's memory.
    - Django's CSRF middleware validates that the CSRF token in the cookie matches the token - received in the request header (or the hidden form field for Django templates).
    - Since the attacker cannot provide the correct header or form token, the validation fails and Django returns 403 Forbidden.
    - As a result, the attacker may be able to cause the browser to send cookies, but they cannot successfully perform authenticated state-changing operations because they cannot satisfy the CSRF validation.

### Serialization: Data Exchange and Storage formats
    Why serialization matters?
        Applications need to exchange and store structured data efficiently
        Serialization converts complex objects into a format that can be easily transferred.
        Used in APIs, databases, caching, and distributed systems
    
    Deserialization:
        Converting it back to an object

    Essential for distributed systems and inter process communication
    
    Explanation:
    The challenge is that computers work with in-memory objects but networks and storage systems needs data in a transferable format
    That gap is exactly solved by serialization
    Serialization converts complex application objects into a standard format that can be transmitted, stored and reconstructed elswhere.
    Without serialization, communication between services, platforms and programming languages would be difficult and inefficient
    you encounter serializer everywhere in system design
    APIs serializes data before sending responses, databases store serialized represention of objects, caching systems use this to persist data in memory,and distributed system rely on it exchange infromation across the services

    Now as system grows and traffic increases the choice of serialization format directly impacts performance, bandwidth usage, storage efficiency and interoperatability

    when the data reaches the destination the deserialization performs the revers operation, reconstructing the original object so that the application can work with it as if it were created locally
    This capability is fundametal to modern distributed systems

#### Common Serialization Formats
    JSON - Human Readable, widely used in REST APIs
           simple key-value structure, easy to parse
           Text based, large in size as compared to binary formates
    XML - Structured but verbose, used in legacy systems
        Tag based markup language, used in legacy systems and configuration files
        More complex than json but supports rich data structures
        Verbose, leading to larger payload
    Protocol Buffers(Protobuf) - Compact and efficient, used in gRPC
        Binary format developed by google
        Faster and smaller than json/xml, but requires schema defination
        Used in gRPCs for high performance APIs

    json optimizes for simplicity and interoperability, XML for structure and validation and protobuf on performance and scalability

#### Readability vs efficiency vs compactability
    Readability: JSON & XML are human reable but inefficient
    Efficiency: Protobuf & Avro are compact, reducing bandwidth usage (no longer human readable requires tooling to read)
    Compatability: XML support schema evolution, JSON has limited support

    Serialization in APIs
        Rest APIs mostly uses JSON
        gRPC APIs use protobuf for efficiency
        XML is still used in SOAP-based web services
    Serialization in caching and Data storage
        Redis and Memcached: Store serialized json/protobuf data.
        Databases: NoSQL databases like mongodb use BSON(Binary JSON)
        Big Data: Protobuf is used for efficient storage and schema evolution
#### Summary:
    Serialization enables efficient data exchange and storage
    Choose right format based on performance, readability and compatability
    Json for APIS, protobuf for efficiecny, Avro for big data
    Impacts bandwidth, storage efficiency and processing speed

### CORS: Cross Origin resource sharing
    Why CORS matters? 
        The problem: Browsers enforce Same Origin Policy(SOP), blocking cross origin requests by default.
    The Need for CORS
        Modern webapplications rely on APIs hosted on different domains (eg. frontend on app.com and api on api.com)
        CORS is a mechanism that allows secure cross origin communication
    
    How CORS works: Request and responses
        CORS is server driven -  the server must explicity allows access
        Two types of request:
            simple request: GET, POST(without custom headers)
            preflight requests: Needed for PUT, DELETE, or custom headers
        CORS Headers control:
            Access-Control-Allow-Origin(which origins can access)
            Access-Control-Allow-Methods(allowed HTTP methods)
            Access-Control-Allow-Headers(custom headers that can be sent)
    
    Preflight requests and CORS headers
        Some requests require preflight checks(sent via OPTIONS request)
        Browser first sends a preflight request before sending the actual request
        If the server responds with the valid CORS headers, the browser allows the request
        Key headers:
            Access-Control-Allow-Origin: https://example.com
            Access-Control-Allow-Methods GET, POST
            Access-Control-Allow-Headers Authorization, Content Type
    Common Security risks
        Overly permissive CORS( Access-Control-Allow-Origin:*)
        Allowing credentials with *
        leads to security vulnerabilities
        Exposing sensitive APIs via improper CORS settings
    Mitigation Strategies:
        Use a whitelist of trusted origins instead of *
        Set correct CORS policies for different API endpoints
        Use reverse proxys or API Gateways to handle CORS securely
    How API Gateways and reverse proxies help?
        Reverse Proxy handle cross origin requests internally to avoid CORS issues.
        API Gateway enforce CORS policies centrally, ensuring security and consistance
        Both improve performance by reducing unnecessary browser preflight requests.
    
    Explanation:
        Instead of removing browsers security, it allows servers to explicity declare which origins are allowed to access their resources.
        CORS provides a controlled way to selectively grant access to some domains.
        Creating this balance between security and flexibility is key to build modern web applications that comminicate safely across domains

        CORS always feels like a browser feature, it is actually controlled by server
        The browser simply enforces the rule, when a cross-origin request is made the server must explicity tell the browser wheather the request is allowed or not.
        For straight forward operations like GET, post the browser sends the request directly
        when a operation could potentiallly modify the resource, such as put or delete request or custom header involved the browser becomes much more cautious.
        Before sending a actual request the browser sends a preflight check using options request.
        The server responds with it cors policy and only if the policy permits the operation the browser will processed with real request.
        The decision is driven by set of response headers.

## Scalability in System Design
    Scalability is the ability of a system to handle an increasing amount of work or its potential to accomodate growth.
    It ensures performance, reliability and availibity under growing load.

    why do systems need to scale?
        User base growth(eg. Launching in new regions)
        Increasing data volumes(eg: IoT analytics)
        Peak events(eg: Black friday sale, ticket sales)
        Avoid service degradation or downtime
        Meet performance SLAs
    Types of scalability
        Vertical Scaling: Add more CPU/RAM to one server
        Horizontal Scaling: Add more servers to distribute the load

    Explanation:
    Maintaing good user experience as demand increases.
    The systems ability to grow as the business grow with redesign of system
    Growth can come in any form more users, more requests, more data and more transcations.

    Vertical scaling offers simplicity
    Horizontal scaling offers greater growth potential and resilience.

### Common challenges in scalability
    Latency:
        Delay between request and response
        Causes: Network hops, slow db queries, synchoronous calls
        Amplified in microservices/distributed systems
    Bottlenecks:
        One slow component = System wide slowdown
        Example: DB locks, memory limits, single threaded processing
        Hard to predict as system grows
    Downtime:
        More nodes = more failure points
        Updates, redeployments, scaling events can cause outages
        High availibity becomes harder
    Cost:
        Infrastrucute isnt fee - CPU,RAM, bandwidhth, etc.
        Autoscaling without limits - budget nightmare
        Over provisioning = wasted speed

    Explanation:
        Every network call, db query, every service to service call adds latency
        In distributed system a single user request may pass through mulitiple servers before a response is returned, making latency a critical business concern
        No matter how scalable our architecture looks, one overloaded component can limit the performance of entire system
        A busy database, resource constraint server, or sequential processing step can become the point where growth starts to break down
        Scaling also increses downtime, More servers, services and dependencies. All this means more potential failure points.
        Deployment infrastructure changes, and scaling events must carefully managed to maintain high availibility.
        Adding capacity increases performance, but excessive scaling can quicky drive infrastructure costs beyond what the business can justify

### Vertical, Horizontal and Diagonal scaling
    Vertical: Upgrade one machine
        Upgrades servers CPUs, RAM, Disk
        Easy to implement(less complex)
        Limits: Physical Cap, risk of single point of failure
    Horizontal: Add more machines
        Add more nodes to the distributed traffic/load
        Requires load balancer, stateless design
        Complex setup (coordination and replicaiton)
    Diagonal: Start vertical then go horizontal
        Hybrid approach: start vertical add horizontal as needed
        Common in cloud native apps
        Cost effective + long term ready

        In the diagonal scaling it start with small to control cost, then automatically add capacity as demand increases, giving teams flexibility without requiring large upfront infrastructure investment.
    
    Strategy    Cost    Complexity  Performance
    Vertical    Low-mid Low         Medium
    Horizontal  High    High        High
    Diagonal    Medium  Medium      High

    Real world examples:
        Twitter: Moved from monolith -> horizontal scaling(microservices)
        Small Startups: Vertical scaling for MVP
        AWS lambda apps: Start diagonal with autoscaling
    When to choose:
        Startups: vertical(cheaper, simpler)
        Scaling apps: horizontal(resilience + capacity)
        Cloud native: diagonal(Flexibity + cost balance)
### Understanding load balancers: Types, Algorithms and cloud solutions
    Load balancer is a intelligent traffic distribution system that works between users and application servers. Instead of allowing one machine to handle everything, requests are spread of multiple servers, improving resource utilization and preventing overload.The result is better response time, more consistant user experience.
    Improves resilience too, In production, servers fail, deployments go wrong and infrastructure issues occur. A load balancer continously checks server health and automatically routes traffic from unhealthy instances, helping the system remain available during failures
    As demand increases we can add more servers without chaning how users access the applicaiton.This allows capacity to grow incrementally rather than a single machine

    Why load balancing is needed?
        High avalibility: Ensures System uptime even under high traffic
        Traffic distribution: Spreads requests evenly across servers
        Prevents overload: Avoids overburdening a single server
        Improves Performance: Reduces latency and enhances response times.
        Handles Failures Gracefully: Redirects traffic in case of server failure
        Supports scalability: helps scale systems efficiently
        Example: A high traffic e commerce site uses load balancing to handle peak hour requests
    
### Types of load balancers
    Based on layer
        layer 4(Transport layer): 
            - Operates at TCP/UDP level, distributing requests based on network level data
            - They only look at information such as IP address and ports for making routing request without inspecting the actual request.Because they process less information they are extermly fast and often used for high throughput and low latency work load
        layer 7(Application layer): 
            - Operates at http/https level, making routing decisions based on request content
            - They can examine URLS, headers, cookies and other request attributes to make more intelligent routing decisions. For example a request to /checkout service may be routed to dedicated transcation service, while a request to /product is sent to different background server. It comes with additional processing overhead, but it enables much more smarter traffic management

    Based on Deployment:
        Hardware load balancers: specialized devices(F5, Citrix NetScaler)
        Software load balancers: Ngnix, HAProxy, Envoy
        Cloud based load balancers: 
            Cloud offers fully managed load balancers
            AWS Elastic load balancer(ELB), Google cloud Load Balancing
### Load balancing strategies
    Static Load balancing:
        Round Robin: Distributes requests sequentially to each request
            works well when servers have similar capacity and workload is predictable
        Least connections: Direct traffic to the server with the fewest connections
        Ip hasing: Routes request based on client IP.
    Dynamic Load balancing:
        least Reponse time: Sends requests to server with the fastest response
        Adaptive Load balancing: Uses realtime monitoring to make decisions(cpu, server health)
        Weighted Load balancing: Assigns different weights to servers based on capacity
    
    The problem with static load balancing is that they assume system state is relatively stable. In production environment that is rarely true. Traffic patterns change servers experience different workloads, and infrastructure conditions continously evolve

    Instead of following predefined rules the dynamic load balancer make decisions based on real time conditions, it provides better resource utilization, resilence as system becomes larger and more unpredicatable

#### Choosing right load balancer
    layer 4 vs layer 7
    Scaliable needs: matching right load balancer for traffic volume
    Security concers: SSL termination and DDoS protection
    Use cases:
        Ngnix/HAProxy for web applications
        AWS ELB for cloud native applications
        Hardware load balancers for enterprise data centers
#### Summary
    Load balancing enhances scalabilty, reliability and performance
    Different types exist based on layers and deployment models.
    Choosing right strategy depends on traffic patterns and system needs
    Essential for high available and resilient architectures

### Autoscaling and best practise in cloud
    What is autoscaling?
        Autoscaling = automatic adjustment of compute resources based on load
        Ensures performance, availiabilty and cost efficiency
        Common in microservices, webapps, and event driven systems
        Main goal: Monitor workload, make scaling decisions and provision resources automatically.

    Autoscaling continously monitor demand and automatically adjusts the compute capacity, wheather adding instances during traffic spike or removing them when demand drops.
        The goal is not just handling users it is about maintaining perfect balance between perforamce, avaliability and cost.

    How autoscaling works?
        Triggers:
            CPU usage
            Memory
            Request Rate
            Queue length
        Types:
            Horizontal Scaling: Add/Remove instance
            Vertical Scaling: Resize a single instance
        Scaling policies:
            Reactive(based on threshold)
            Predictive(based on trends)
    
    A platform that continously monitor key signals such as CPU utilization, Memory Usage, request volume, or queue depth to understand the current workload.
    When those metrics indicate increasing demand, the system decides wheather to scale horizontally by adding more instance or vertically by upgrading the resource of exisiting resource.
    
    Reactive polices respond to realtime conditions, such as CPU usage exceding a predefined threshold. They are simple and widely used, but they react only after the load has already increased.
    Predictive Policies goes one step ahead further by analyzing the historical pattern and forecast future demand, allowing capacity to be added before traffic spikes even occur.

    Autoscaling across Cloud providers
    AWS- Auto Scaling for EC2, Lambda, ECS, EKS
    Azure - Autoscaling via VM Scale sets, App services, AKS
    GCP - Autoscaling with MIGs, Cloud Run, Functions, GKE

    Monitoring and Proacive scaling
        Use metric like:
            CPU,Memory, Network
            Queue Depth, Custom KPIs
        Proactive scaling:
            Predictive algorithms(based on ML or trends)
            Scheduling scaling(known traffic patterns)
        Tools: Cloud watch, Prometheus + Grafana, Azure Monitor, GCP operations
    Cost optimizations:
        Avoid over provisioning - scale just enough
        Use spot/preemptible instances for batch workloads
        Apply resource limits and quotas
        Rightsize regularly based on actual usage
        Use auto pausing or scale to zero features for idle services
## Storage - Database and Storage
### Storage in system design and CAP theorem
    All system generate and consume data - storing is essential
    Storage impacts performance, reliability and cost
    Persistant storage enables everything from user profiles to search history to analytics

    Explanation:
        The storage choices might effect system response time, system reliability, operational cost, scalability limts and even the user experience
        A fast applicaton with slow storage will eventaully become bottleneck while unreliable storage can turn minor failure into permanent loss.
        Think about the features users interact with every day - profiles, preference, shopping cards, search history, analytics and audit logs.
        All this depens on persistant storage that reliably retain and server data over a long periods of time.
    
    Structured vs unstructured data
        Structured: Rows/Columns, predefined schema(eg. SQL schema)
        Unstructured: No schema, flexiable format(eg:images, videos, logs)
    
    Explanation:
        Structured data is organised and follows predefined schema. Think about user accounts, orders, payments. Every rows follows same format, which makes quering, filtering and joinin data extremely efficient.
        This predictability is why relational databases are so effective for traditional systems.
        Unstructed data is every different content such as videos, documents, applicaiton logs, and audio files does not fit into rows/columns.
        The format is flexible but flexibility comes with different storage and retrival challenges. Instead of complex sql queries this files are typically stored in object storage systems, and accessed through metadata or specialized indexing mechanisms.
        An ecommerce application might store custom and order details in relational database while product images, invoices, and user generated content live in object storage.
    
    Categories of storage
        Database storage(SQL, NOSQL)
        Object storage(eg: S3)
        File storage(eg: NFS)
        Block storage(eg: EBS)
    
    Explanation:
        - Data base storage is optimized for application data that needs to be queried, updated and related to other data.
        This is prefered by traditional applications
        - Object storage takes different appraoch instead of storing data in tables or files system, it stores objects which can scale into billions of items
        This is prefered by images, videos, documents, backups and logs archieves, where durability and massive scale matter more than low latency updates. 
        - File storage provides the familier folder and file hierarchy that operating systems and many legacy application might expect.
        It is useful when muliple servers or applications need shared access to the same files through a standadized file system interface.
        - Block Storage - Storage is preserved as raw disk block, giving applications direct control over how data is organized. This delivers high performance and low latency required by databases, virtual machines, and other IO Intensive workloads
    
#### Storage Properties
    Durability - Data persists even after failure
    Availability - Data can be accessed when needed
    Consistancy - Every read returns the most recent write
    (Optional)Atomacity - Operations are all or nothing (relevent in transcational storage)

#### Tradeoffs in storage system
    Scalability vs Reliability vs Performance
        Scale(can handle growth)
        Reliability(resistant to failure)
        Performance(speed of reads/writes)
    Explanation:
        At high level architects often balances this scalibilty, reliability, performance.
        For example: Replicating data across muliple servers improves Reliability, but it can introduce additional latency and reduce write performance.
        Optimizing for extermely low latency access might require keeping data closer to user, but that can make consistance and realiability harder to maintain at scale.
        A banking application may priortize reliability and consistance over raw speed, while a social media feed may prioritize scalabilty and responsiveness.
### The CAP Theorem
    CAP Theorem is mainly about: 
        Partition Tolerance is not really optional in large scale distributed systems.
            Network fail, links breaks, and regions become temporarly isolated. Since partitions are inevitable, realworld systems are effectively choosing between consistancy and avaliability during thos failures

    In a full distributed system, you can only gurantee 2 of the 3
        - Consistancy - Every read gets the latest write
        - Availability - Every request recives a response
        - Partition Tolerance - System continous dispite network failures
        No system can have all 3 all the same time
    Note: Since network partitions are unavoidable, especially at scale, real world systems must choose between Consistancy and Availability during a partition.

    Explanation:
        CAP tells when a distributed system experiences network partition, meaning some nodes can no longer communicate reliably, you cannot gurantee both perfect consistancy and full availability.
        - Consistancy: Means every users see the latest commited data regardless of which node they are connected to.
        - Availibity: Means every request receives a response, even if some parts of the system are experiencing the issues.
        - Partion Tolerance: Means That the system continously operating despite network failures between nodes.
        Partition Tolerance is not really optional in large scale distributed systems.
        Network fail, links breaks, and regions become temporarly isolated. Since partitions are inevitable, realworld systems are effectively choosing between consistancy and avaliability during thos failures
        For example banking system may favor consistancy, preferring to reject requests rather than risk showing incorrect account balance.
        A social media feed, on the other hand, might favour availibility, allowing users to continue interacting even if some data is temporarly stale.
        Under normal conditions systems provide both consistancy and availability.
        The tradeoff only occurs when a network partition occurs.
        CAP is ultimatly about how a system behaves during failure, not when everything is working perfectly.

#### Types of systems Based on CAP trade offs
    CP(Consistancy + Partition Tolerance)
        Prioritize data correctness over availability
        During a partition, the system may reject requests to avoid inconsistant reads
        Not always available, but when it is - data is guranted to be correct
        Example: HBase: Strongly consistent. If a node cant confirm a write across replica, it wont serve it - even if it means being unavailable briefly.
        When to use: Financial systems, banking apps, anything where data integrity is critical
    AP(Avalibility + Parition Tolerance):
        Prioritizes system uptime over consistancy
        During a partition, the system will serve requests,even if they return stale or eventually consistant data
        Example: Dynamo Db: Inspried by Amazon Dynamo Model, which uses eventual consistancy by default for high availability
        When to use: Social media feeds, product catalogs, content delivery - where being up is more important than perfect accuracy
    CA(Consistancy + Availibility):
        Only possible if no network partitions ever occur - i.e, in single node or tightly coupled systems
        In practise, not archievable in distributed systems that need to tolerate network faults
        Example: Relational databases(like postgresql) is standalone mode(not distributed) could be considered as CA
    
    Explanation:
        CP: This systems prioritize data correctness above every thing, During network partition they may refuse reads or writes rather than risk returing incorrect data.
        From users perspective the system might appear temporarly unavailable. But the data you do recieve is guranted to be correct.
        AP: This systems choose to remain operational even when parts of the network cannot communicate, Networks continous recieving responses but some of those responses may remain stale util replicas syncronize data
        This tradeoff's works well for workloads like social media posts, product catalogs, recommendation and content platforms where a slightly outdated response is usually acceptable
        CA: In theory this systems provide both correct and continous availability. The catch is that this only work when network partitions doesnot occur, since network partitions are evitble, it truly works at single node system or tightly coupled deployment rather than large scale distributed architectures.

### Database models SQL vs NOSQL
    What is a database?
        A structured way to store, retrieve and manage data
        Supports persistant storage and efficient quering
        Core component of backend systems, from small apps to global platforms
    
    Explanation:
        A database provides persistant layer, giving us a reliable way to store information and retrive it efficintly when application needs it.
        But databases are more than a storage, They allow us to query, filter, update and manage data in strucuted way, which becomes critical as application grows.
#### Intro to Relational databases(SQL)
    Data stored in rows and columns
    Enforces strict schema(structure)
    Uses SQL(Structured query Language) for queries

    Explanation:
        Relational databases have been the backbone of enterprise applications for decades because they provie highly structured and predictable ways to manage data. Instead of storing data in loosely organized records, they organize data into tables made of rows and columns, making the relationship between different pieces of data explicit and every easy to manage.
        Schema first approach makes SQL Db powerful
        Before data is stored, we define its structure, what fields exist, their data type and the rules they must follow
        This descipline helps to maintain data quality and consistancy as systems grow
        The major advantage is quering power. Using sql engineers can filter, aggregate, sort and combine data across multiple tables with remarkable flexibility.
    
    Core concepts of Relational Databases
        Schemas: predefined strutures(tables, columns, datatypes)
        Joins: Combine data across multiple tables
        ACID Properties:
            Atomicity: all or nothing
            Consistancy: data integrity maintained
            Isolation: transcations doesnot interfere(prevents concurrent transcations from corrupting each other work)
            Durability: Changes survive system failures(ensures that commited changes survive crashes and system failures)
    
    Limitions of Relational Databases
        Not ideal for
            Rapidly changing or schema less data
            Large-scale horizontal scaling
            Flexible or nested data(eg: JSON blobs)
    Explanation:
        Relational databases excel on a single powerful server, but distributing data across many machines introduces complexity around sharding, repliacation and consistancy
        As traffic reaches internet scale, scaling a traditional sql database becomes increasingly difficult and operationally expensive.
        They can also feel less natural when working with highly flexible or deeply nested data

#### Into to NoSQL
    Designed for flexibility and scale
    Schema less for dynamic schema
    Types:
        Document(Mongo Db)
        key-value(Redis, Dynamo Db)
        Columnar(Cassandra, HBase)
        Graph(Neo4)
    Explanation:
        No SQL databases prioritise flexibility, scalability and performance for specific type of work loads
        Many No SQL databases allow data structures to evolve without requiring rigid schema definition upfront.
        This makes them well suited for rapidly changing applications, user generated content, event data and other scenarios where the shape of the data is not always predictable
        NoSQL is not a single technology, It is a family of database models, each optimized for different purposes.

        - Document databases store rich JSON like structures and ideal for flexible application data.
        - Key-value focus on extermly fast lookup and very low latency
        - Columnar databases focus on high write throughput and large scale distributed workloads
        - Graph databases specialize in traversing complex relationships between entities

    No SQL deepdive
        Document databases:
            JSON like structures (key-value pairs, nesting supported)
            ideal for content management, user profiles
            Example: Mongo db
        Key value databases:
            Simple, fast, key-based lookup
            High performance, low latency
            Example: Redis, Dynamo DB
        Columnar databases:
            Store data by column, not row
            Optimized for analytics queries over large datasets
            Example: Cassendra and HBase
        Graph databases:
            Stores entites and relationships as nodes and edges
            Efficient for hightly connected data(eg: social networks)
            Example: Neo4j
    
    Base properties in NoSQL
        Basically Available: Always returns a response (even if stale)
        Soft state: System state may change over time
        Eventually consistant: Data will be consistant...eventually

    Explanation:
        The key idea behind base is that in large scale distributed systems, being available to users is often more important than having every node reflect the latest update immediately.
        If a user requests data, the system responds even during failures or network partitions though that data may not be the most updated to date version of data.
        Because data is replicated across mulitple nodes, different replicas can temporarly hold different values this is soft state
        A system will continously converging towards a synchorinzed view of the data.Overtime updates propate through a cluster and all replicas eventually agree on the same value a property known as eventually consistancy
    
    SQL tends towards CP, NoSQL tends towards AP or Base

#### When to choose what?
    when to use SQL
        Complex queries and relationships
        Strong consistancy needed
        Structured and well known schema
        Ex: Banking, ERP, Inventory Systems
    when to use No SQL
        High Scalability needed
        Flexible or evolving data structure
        Low-latency or high volume operations
        Ex: IoT,Recommendation Systems, Caching, logs

### Advanced database Topics: Sharding, Replication and Polyglot Persistance
#### Scaling strategies - SQL vs No SQL
    Vertical Scaling(scale up) - Traditional SQL databases
        How it works: By adding more CPU, RAM, or SSD to a single database server
        Common with: Relation Db's like Postgresql, MySQL, Oracle
        Pros:
            Simple architecture
            Strong consistency(ACID gurantees)
        Cons:
            Limited by hardware capacity
            Cost grows non-linearly
            Risk of single point of failure
    Horizontal Scaling:
        How it works: Add more database nodes to distribute data and load
        Common with: NoSQL DBs like MongoDb, Cassandra, Dynamo Db
        Pros:
            Elastic Scalability
            Handles large scale traffic and big data
            Better fault tolerance
        Cons:
            Complex architecture
            Weaker consistency(often eventual)
#### What is replication?
    Copying data from one database node to another for redundancy and performance
    Benefits:
        Fault tolerance
        Read performance improvement
        Data availability
    Trade offs in real world systems(CAP theorem)
        Replication may favor availability
        Strong consistancy may sacrifice availability
    
    Explanation:
        Since data is maintained in one database, if that machine fails or becomes overloaded, or losses connectivity, the entire application is at risk.
        Replication solves this exact issue by maintaning copies of the same data across multiple database nodes.
        The immediate benefit is reslience, if one node becomes unavailable, another replica can continue to serve the request.
        Thereby significantly improving fault tolerance and overall system availability
        Replication also help with scale, In many applications read traffic far exceeds write traffic.
        By distributing read requests across multiple replicas, we can increase throughput without continously upgrading a single database server.
        The moment the data exist on multiple nodes, keeping every copy perfectly syncronized becomes challenging, especially during network failures or partitions
        As a result many real world systems prioritize availability and allow replicas to be temporarly out of sync, leading to eventual consistance.
#### Leader follower replication
    how it works?
        Writes go to the leader
        Read from followers
    Consistancy Considerations:
        Asynchronous replication = possible lag
    
    Example:
        In this model leader acts a single point of truth. Every write, wheather it is write, update, delete is first commited to leader
        Those changes are propagated to one or more followers which primarly serve read requests
        This allows system to scale read traffic efficiently without overwhelming the primary database
        As read demand grows, we can add more followers and distribute queries across them.
        In most production systems, replication is asynchoronous to avoid slowing down the writes.That means there is a small delay between the change being commited to the leader and the same change appearing on the followers
        During this window, the users reading from follower may see some stale data
        We gain scalability, performance, and availability but we may sacrifice immediate consistancy
#### Read Replicas
    Use case:
        Scaling ready-heavy workloads
    Difference from lead-follower:
        Often used just for load balancing reads
        Doesnt take part in writes
    
    Explanation:
        They exist primarly to distribute read traffic and improve performance. All writes still goes to the primary database and the replicas simply stay synchoronized with it and serve the queries
        During traffic spikes, additional replicas can often be added with minimal application changes, allowing a system to scale horizontally for reads without redesining the database architecture.
        The tradeoff remains is consistancy, since they synchronize async there a may be a delay in recent change appear.
        This is why critical operations such as viewing a just updated account balance or order status may still need to read from the primary database
#### What is sharding?
    Spliting database across multiple databases to scale horizontally
    why its needed?
        Performance and storage limits of a single node
    Types of sharding
        horizontal sharding: rows are distributed across shards(most common)
        Vertical sharding: Tables or columns are split across shards based on function or access pattern

    Explanation:
        Instead of storing data in one database, we partition it across multiple independent databases called shards
        Each shard owns a portion of the dataset and processes only the request related to that data
        By distributing both storage and work load, the system can continue grow almost indefinitely by adding more shards
        The most common approach is horizontal sharding, where rows are distributed across shards based on the key, key could be user id, customer id or region.
        Vertical sharding takes different approach, Instead of spliting rows, it seperates data by busiess function or access pattern
        For example: User profile, billing data, analytics data may live in different databases
        Once data is distributed, the system must determine where the data live, route requests to the correct shard and handle operations that span across multiple shards
        That adds significant architectural complexity
#### Sharding strategies
    1.Range Based Sharding
        Split by value ranges(e.g: user_id=1-1000)
        Can create hot spots
    2.Hash based sharding
        Distribute using a hash function
        Even distribution but harder to query ranges
    3.Consistent Hashing for resilient hash based sharding
        Traditional hashing breaks when nodes are added/removed
        Consistent hashing solves this: only a subset of keys needed to be remapped when topology changes
        Enables better elasticity and fault tolerance
    4.Geo based Sharding
        Shard by user region/location
        Useful in geo distributed systems
    
    Explanation:
        If new data continously falls in same range, one shared can overload while other shareds remain idle, thus creating hotspots
        This can solved using hash based sharding it will distribute data evenly using hash function
        This produces better load distribution and prevents single shard from bottleneck
        The tradeoff is that data losses natural ordering, making range based queries more complex and often requiring requests to multiple shards
        When a node added or deleted, it forces large amounts of data to be redistributed
        Consistent hasing designed to solve this problem: only a subset of keys needed to be remapped when topology changes
    
#### Polyglot Persistance
    Using different types of databases for different kind of components/services
    why: Each db excels at different things(search, analytics, relations)
    Benefits:
        Better performance
        Optimized storage and queries
    
    Multiple databases means multiple technologies to manage, monitor, secure, backup and maintain
    The goal is to solve different data challenges with most appropriate technology
    
    All ways start with one database when possible, and introduce additional data stores only when a clear scalability, performance, or business requirement justifies the added complexity

### Object Storage in Modern systems
    What is object storage?
        A storage architecture that manages data as objects, not files or blocks
        Each object contains:
            Data itself
            A unique identifier(key)
            Metadata
    Unlike traditional storage, it is scalable, distributed and suited for unstructured data

    Explanation:
        The key idea is that data is stored as a self contained objects rather tha files organized in folders or blocks attached to disks
        Every object combines the actual data, a unique identifier used for retrivel and rich metadata that describes the object and how it should be managed
        This design becomes incredibly powerful at scale because the storage system no longer depends on traditional directory strucuture or fixed volumes
        Instead object lives in namespace and can be distributed across thousands of servers transparently.
        That is why object storage became the default choice for storing massive amounts of unstructured data like images, videos, documents, backups, logs and data lake content
    
    Key concepts in Object storage:
        Object: self contained unit of data
        Bucket: Logical container for storing objects(like folders)
        Metadata: Custom data that describes the object (eg:MIME type, timestamp, custom tags)
    
    Explanation:
        Metadata stores beyond basic data like content type, size and timestamp it also stores application specific attributes like ownership, project information, rentension polices, or access classification
        This additional information allows applications to search, automate,secure and manage data much more intelligently

    Popular Object storage platforms
    Amazon S3: industry standard, rich ecosystem, high durability
    Google Cloud Storage(GCS): Simplified tiers, ML friendly
    Azure Blob storage: Strong integration with microsoft stack
    On prem alternatives(MinIO) of hybrid or cloud native use

    Since object storage can serve files directly over HTTP, it becomes a simple and very cost effective way to host frontend applications, document sites, landing pages, and content portals with out managing webservers

#### Important considerations with object storage
    Performance considerations:
        Latency: Object storage has higher latency than block/file
        Throughput: Designed for massive parallel access
        Consistance: Eventual consistancy in some platforms(eg: s3)
        Access pattern: Suited for write once, read many workloads
    Cost considerations:
        Storage class tiers: Standard, infrequent Access, Archieve(S3 Glacier)
        Charges: Storage, request(GET/PUT), egress bandwidth
        Best practises:
            Use lifecycle rules for archieving/deletion
            Monitor usage and optimize classes

### File system and distributed storage
    What is a file system?
        Defines how data is stored and retrived on disk
        Example: ext4, NTFS, XFS
    Handles file metadata, directories, permissions
    
    Key characteristics of Traditional file system?
        Hierarchical structure(folders/files)
        Limited scalability across machines
        Suited for single node systems
        use cases: Personal devices, small servers
#### What is distributed file system(DFS)?
    Allows file access across multiple nodes
    Ensures redundancy, fault tolerance
    Appears as a single file system to the user
    Key benefits: Scalability and reliability
    Example:
        HDFS(Hadoop Distributed File System) - Big data analytics
    Use cases:
        Big data analytics(eg: Hadoop, spark)
        Enterprise Storage(shared file system)
        Scientific Computing
        Media and backup systems

## Performance Concepts, tools and technique
### Introduction to system performance
#### What is performance in system design?
    Performance = how efficiently a system meets its functionality requirements under load
    Key dimentions:
        Speed: Time to respond
        Capacity: Amount of work handled
        Efficiency: Resource usage under load
    Performance is not a single metric - its multidimentional goal
    performance = speed, efficency and scalability under load

#### Latency vs throughput
    latency
        Time taken to process one request
        Measured in ms or s
        Affects responsiveness
    Throughput
        Number of requests processed per second
        Measured in RPS or TPS
        Affects scalability
    Low latency != High Throughput and vica versa
    Both must be balanced based on use case

    Use case:
        Gaming industries optimizes latency each ms is important
        Large scale analytics, and batch processing platforms are typically focused on maximizing the throughput

    Explanation:
        latency is the waiting time between the request and response
        Throughput is how much work can the system handle over time?, it measures volume of requests or transcations processed per second

        A system might deliver very low latency for a small number of users, but struggle when traffic increases
        A system optimized for a massive through put may process huge volumes of requests while individual requests may take longer time to complete
        We rarly optimize single metrix
#### Scalabilty vs Responsiveness
    Scalability: Ability to handle increased load without performance degradation
        Horizontal vs vertical scaling
    Responsiveness: Systems ability to respond quickly
        Tightly linked to latency
    Good design should ensure responsiveness at scale

#### Measuring Performance
    Performance must be measurable and trackable
        SLA(Service Level Agreement): External Contractual guarantee
        SLO(Service Level Objective): Internal target
        SLI(Service Level Indicator): Actual Metric value
    Example:
        SLA: 99.9% uptime
        SLO: 95% of requests < 300ms
        SLI: Actual measurements(eg: 93% of requests < 300 ms)
    
    Explanation:
        SLA: Represents commitment made to the customer or client
        It defins level of service the business promises to deliver and it is often tied to contractual obligations
        SLO: Sits inside the engineering organization, it translates business expectations into concrete operational targets, things such as response time, avalibity or error rates
        SLOs give teams a measurable benchmarks for sucess and help to prioritize reliability of their work
        SLI: is an actual measurement collected from the system. It tells what is happening in production right now
        By comparing SLI against SLO, engineers can quickly determine wheather the system is meeting expectations or drifting towards a problem

        For example:
            A company might promise 99.9% uptime through a SLA, define an internal SLO that 95% of the requests complete within 300ms and then monitor SLIs to see wheather real world performance is meeting those targets or not
            SLA is a promise, SLO is the goal, SLI is the reality of the system
#### Understanding percentiles
    Mean/Average != useful in tail-latency-sensitive applications
    Percentiles provides better insights
        P50: median
        P95: 95% requests faster than this
        P99: Tail latency - critical for user experience
    Track tail latencies for real world performance insights

    50% Requests -> 45% Requests -> 4% Requests -> 1% Slowest
      <=P50          P50 -> P95      P95 -> P99      Tail latency
    
    Production system often monitor P95 and P99 systems along with average

#### Why performance matters in Modern applications
    Users expect instantaneous responses(esp. mobile/web)
    Poor performance lead to:
        Drop-offs and bounce rates
        Loss in revenue
        System instability under load
    Performance is not a feature, not an afterthrought
    Impacts user experience, cost and reputation

    Explanation:
        Users rarely notice when a application is fast but immediatly notice when application is slow
        Slow applications lead to abandoned shopping carts, reduced engagements, lower conversion rate and higher bounce rate
        Even if functionality is correct, users often percieve a slow application as unreliable
        As traffic grows inefficient system consums more CPUs, memory, storage and network resources increading infrastructure cost while reducing stability

#### Performance Testing overview
    Types of performance Testing:
        Load testing: Normal load conditions
        Stress Testing: Beyond normal limits
        Spike Testing: Sudden large load
        Endurance Testing: Over extended time
    Goals:
        Identify bottlenecks
        Ensure realiabilty under real world scenarios
#### Introduction to Performance monitoring
    Monitoring != Testing - its continous
    Key tools
        APM(eg: New relic, datadog)
        Logs and metrics(eg: ELK, promotheses + grafana)
    Track:
        latency and throughput
        Error rates
        Resource usage(CPU, memory, DB queries)
    Monitoring is about detecting problems early
    A well monitored system allows teams to move from reactive firefighting to proactive operations, identifying performance issues before they impact customers and business outcomes

### Caching for speed optimization
#### Why caching matters?
    Reduces latency by avoiding expensive recomputation or data retrieval
    Eases load on backend services and databases
    Improves user experience and system scalabilty
    Critical in low latency, high throughput architectures

    Explanation:
        Caching becomes important when system starts doing a same expensive work repeatedly, Evey db call, API call, or computation adds latency and at scale, this ms accumulate into a poor user experience
        Frequently accessed data can be directly served from the memory rather than API call or db call
        That is why search suggestions, social media feeds, product catalog, and user profiles often feel instant
        By serving large amounts of requests from cache, you dramatically reduce database load, increase throughput and delay costly scaling efforts
        Caching increases system scalability
        A system that handles 10k requests per second without cache, caching might support times that volume once cache hit rates become high
        In many large scale applications, the cache obsorbs the majority of read traffic, while backend systems only handles the cache misses
#### Types of caching
    Client-side: Browser Memory(eg: localstorage, service workers)
    Server-side: Application level memory or in memory caches like redis
    CDN caching: Static content cached close to users(eg: Cloudflare, Akamai)
    Database caching: Result-set caching, materailized views

#### Caching Strategies
    Write-Though: Write to cache and DB simultaneously
        Data is written and updated simentanoulsy on both cache and the db
    Write-back(write behind): Write to cache, db is updated asyncronously
        Data is first written to cache and then asyncronously to the db
    lazy loading(Cache-aside): Cache is populated only on demand
        Data is explicitly fetched and stored in cache by the application when necessary
    Explicit/manual caching: Developer decides when to cache or evict

#### Cache Eviction policies
    LRU(Least Recently Used): Remove least recently accessed item
        1m ago, 10 min ago, 1 hour ago, 10 hour ago - Remove 10 hour ago content since last access time is 10 hours ago
    LFU(Least Frequently Used): Remove least used item by count
        reel 1 - 300 times, reel 2 - 600 times, reel 3 - 1000 times - remove reel 1 least frequently seen
    FIFO(First In, First Out): Remove oldest item added
    TTL(Time to Live): Automatically expires items after a fixed time duration

#### Redis Overview
    In-memory key-value store for ultra-fast access
    Supports TTLs(Time to Live), persistance, pub/sub
    Used for caching, queues, sessions, leaderboards, etc
    Open source, widely adopted

    Explanation:
        It solves the issue accessing data at scale
        While databases are optimized for durabilty and complex queries, Redis is optimized for speed.
        By keeping data in memory, it can serve requests in microseconds, making it ideal for performance critical workloads
        Pub/sub enables light weight event driven communication between services, and it has persistance options that provides balance between speed and durabilty when data needs to service the survive restart
        Redis oftens appears in multiple places within same architecture, It can sit in front of db as cache, it can act as session store of the web application, It can power background job queues, or it can maintain realtime counters and leaderboards where fast updates are very essential
        The operational overhead is relatively very low, and virtually every major platform offers managed redis services
        When needed high performance layer architects choose redis
#### Real world caching examples
    CDN: Cache Static assests(image, JS, css)
    Product Page data: Cache popular catalog queries
    User sessions: Stored in redis for fast access
    Search Results: Frequently repeated queries cached
    API response caching: Microservices avoid recomputations
    



