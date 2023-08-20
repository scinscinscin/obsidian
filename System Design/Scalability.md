**Common Scalability Issues**
 - handling more data - companies become greedier about storing more data and not deleting it
 - handling higher concurrency
	 - servers have a limited amount of CPU and execution threads. It is even more difficult as you may need to sync parallel execution of your code to ensure consistency of your data
	 - higher concurrency means more open connections, more active threads, more messages being processed at the same time, and more cpu context switches
 - handling higher interaction rates
	 - measures how often your clients exchange information with your servers. 

Scalability is defined by a combination of these requirements. 

Scalability of a software product may be contained by how many engineers are working on the system. As your system grows, you will need to consider organizational scalability, you will not be able to make changes or adapt quickly enough. If your system is highly connected, you may struggle to scale your engineering team since everyone will be working in the same codebase. 

**Single server configuration**
 - the entire application runs on a single machine
 - it performs all the duties necessary to make your application run.
	 - Database management
	 - serving images and dynamic content from within your application
	 - Virtual private server
		 - A virtual machine for rent
		 - It is hosted together with other vps instances on a shared host machine
		 - Behaving like a regular server, but is cheaper. 
	 - Shared hosting is the cheapest solution where you purchase a user account with admin access, however it is too limiting
 - Each user creates additional load on the servers, consuming more resources including memory, CPU time, and disk input / output.
 - DB queries may begin to slow down due to requiring more CPU, Memory, and IO
 - User interactions require more system resources due to new functionality

**Vertical scalability**
 - Upgrading the hardware and network throughput
 - Does not have to change the way that the application works

**Isolation of services**
 - moving different parts o=f the system to separate physical servers by installing each type of service on a separate machine. 
 - Only a slight evolution that doesn't take you far because there is no more room to grow once you deploy each service type on a separate machine
 - it slowly increases the number of servers that can share the load. Servers are hosted in third party datacenter. 
 - Each server has a certain role, such as a webserver / data server / FTP or cache
 - You can distribute the load among more machines than before and scale each of them vertically as needed. 
 - Agencies will host many tiny websites for different clients on shared web servers.
 - Split your monolithic web app into distinct functional parts and host them independently. This process is called functional partititoning.

**Cache** - service focused on reducing the latency and resources needed to generate the result by serving previously generated content. 

**Using a CDN**
 - it becomes beneficial to offload some of the traffic to a cdn service
 - takes care of global distribution of static files like images / js / css and videos.
 - clients that need to download static content connect to one of the servers owned by the cdn provider instead of your servers. If the CDN doesn't have the requested content yet, it asks your server for it and caches it from then on.
- reduce the bandwidth that your servers need, requiring fewer web servers to serve your application's static content.
- can benefit from resource locality, speeding up load times
	- can optimize the way they serve the content cheaper than you could
- is a good strategy for startups since we can just rely on the external service to scale for us

**Horizontal scalability**
 - much harder to achieve and has to be considered before the application is built.
 - it requires significant development effort.
 - "running reach component on multiple servers and being able to add more servers whenever needed"
 - increased capacity by adding more servers, thus considered the holy grail of scalability
 - pays of at a later date and might cost more because they are more complex and require more work

**Round robin DNS** - allows for resolving a single domain name to multiple IP addresses
	each time a client asks for a domain resolution, dns responds with one of the ip addresses
- different clients may be connected to different servers without realizing it. Once a client receives an ip address, it will only communicate with the selected server.

**You will need more than 1 datacenter at some point**
 - a single datacenter can ost plenty of servers but clients located on other continents will have a bad UX
 - more than 1 DC allows you to plan for rare outage events
 - You can use geodns to plan for it
	 -  domain names are resolved to different ip addresses based on the location of the client with the goal to direct the consumer to the closest data center to minimize network latency
 - We can also use multiple edge-cache servers around the world to reduce the network latency even further. 
	 -  they are most efficient when they act as simple reverse proxies caching entire pages but they can provide other services
	 - they can partially cache the HTTP traffic (can serve entire pages or fragments of http responses)
		 - The server can decide to serve the page from cache
		 - Assembly missing pieces of the page by sending background requests to the server
		 - decide the page should be loaded fully from the web servers

# The front line
 - Components that the user's devices interact with directly
 - these components should not have any business logic and the goal is to increase capacity and allow scalability

**Load balancer**
 - software or hardware component that distributes the traffic coming to a single IP address over multiple servers, which are hidden behind the load balancer.
 - used to share load evenly among servers and to allow dynamic addition and removal of machines. New servers can be added at any time without service disruption
 - they can go behind frontend cache servers or directly behind frontend app servers

## Web application layer
 - generating the actual html of our web application and handling the clients' HTTP requests
 - Lightweight framework with minimal amount of logic
 - The goal is to render the user interface.
 - Handle user interactions and translate them to internal web services calls.
 - they are easy to scale since they are completely stateless.
	 - adding more capacity is simple as adding more servers to the load balancer pool

## Web services layer
 - makes it easier to create functional partitions
 - we can make web services specializing in certain functionality and scale them independently
 - the comm. protocol between front-end and backend is usually REST or SOAP.
 - they should be easy to scale as long as we keep them stateless.
	 - adding more machines to the pool
 - It has become popular to expose integrations to third parties, which is why web services are deployed in parallel to the front-end servers rather than behind them.

**Object cache servers**
 - reduce the load on data stores and speed up responses by storing partially precomputed results
**Message queues**
 - Postpone some of the work at a later stage and delegate the work to queue worker machines
 - clusters of batch processing services or jobs running on schedule
 - asynchronous notifications / order fulfillment

## Data persistence layer
- most difficult to scale horizontally, with it being a rapid area of development
- multiple data stores are used by the same company to leverage their unique benefits and to allow better scalability
- Search engines have become popular due to their rich feature set and existence of good open source projects. 

## Data center infrastructure
 - we managed to get the ability to share load among multiple servers
 - traffic is reduced and only part of it hits the frontend servers
 - by adding easily scalable layers on top of the data layer, we can scale the overall system in a cost effective way

**Domain model**
 - the core functionality of the app in the words of business people
 - key terms, actors and operations without caring of technical implementation
 - editors / readers / manipulation of posts
 - Oblivious to hardware and software implementation and is a tool to create a mental picture of the business problems our app is supposed to solve
 - can be visualized using a use case diagram
	 - a simplified map that defines who- the users of the system are and what operations they need to perform
	 - Actors represented by humanoid icons, actions that actors perform and a high level structure of how different operations relate to each other.

# Frontend
it should have the single responsibility of becoming the user interface. **It should be the layer translating between public interface and internal service calls**. 
 - internal service calls can refer to public API calls with the frontend being a web client
 - by keeping the frontend stupid, we can reuse more of the business logic, avoiding the risk of coupling it with our presentation logic.
 - Presents the functionality of the system to the customers and should not be the heart or the center of the system.
 - We can also scale frontend servers independently as they will not need to perform complex processing or share much state, but may be exposed to high concurrency challenges.

Frontend code will be closely coupled with the framework of choice and is constrained by the user interface / ux requirements and the tech used.
 - They will be developed in a way that allows comms over http.
 - Templating and ajax are specific problems. Keep them separated from your main business logic to allow for fast and independent changes. 

Frontend should not be aware of any databases or third party services. Projects that allow business logic in the frontend code suffer from low code reuse and high complexity.
	we should prefer to cache an entire HTML page aside from just the database query that was used to render the HTML

## Web services (backend / API)
 - where most of the processing has to happen, and where most of the business logic should live

**Service oriented architecture**
 - loosely coupled and highly autonomous services focused on solving business needs
 - all services must have clearly defined contracts and use the same comm protocols.
 - they must specialize in a narrow set of business needs.

**Multilayer architecture**
 - divide a functionality into a set of layers
 - components in lower layers expose an API that can be consumed by clients residing in the layers above.
 - Never allow lower layers to depend on the functionality provided by upper layers
 - Layers enforce structure and reduced coupling as components in the lower layers become simpler and less coupled with the rest of the system

**Hexagonal architecture**
 - Logic is the center of the architecture and all the interactions with the data stores / clients / and other systems are equal.
 - There is a contract between the business logic and non business logic component but there is no distinction between the layers above and below.
 - Users interacting with the applications are no different from the database system that the application interacts with. They both reside outside of the application business logic and both deserve a strict contract.

**Event-driven architecture**
 - different way of thinking about actions
 - reacting to actions that already happened
 - Whenever we interact with other components, we announce things that have already happened and continue with our processing.

We build abstractions to hide complexity, limit dependencies and scale independently. The ideal is to have all services be completely isolated from each other to be able to scale independently, however this is impossible as integrations are what solve business needs.