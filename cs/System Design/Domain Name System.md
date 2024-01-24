 - clients need to find your server's ip address before they can connect to it.
 - DNS is used to resolve domain names like ejsmont.org to an ip address
 - third party hosted service instead of deploying your own dns infrastructure
	 - web hosting company that supports dns entries for thousand of domains.
	 - gain flexibility and save money on the hosted service itself
	 - dozens of large dns hosting companies which are cheap, reliable and scale well
 - Amazon Route 53
	 - allows to redirect clients to the closest data center based on latency ("latency based routing")

## Load balancers
 - DNS was sometimes used to distribute traffic over more than one web server.
	 - issues: not transparent to clients
	 - Cannot remove a server out of a rotation because clients might have its ip address cached
	 - Cannot add a new server to increase capacity snice clients that have resolved it will keep connecting to the same server
 - Load balances should be the entry point to the data center as they will allow you to scale more easily and make changes to your infrastructure without affecting your customers
	 - all the traffic is routed through the load balancer and thus the structure of the data center is hidden from the clients
	 - Hidden server maintenance - can take a server out of the pool and wait for all connections to drain, then shutdown the web server without affecting a single client to perform rolling updates.
	 - Seamlessly increase capacity
	 - Efficient failure management
	 - SSL offloading - a technique where all ssl encryption work is done on the load balancer and the rest of the connections internally are unencrypted.
		 - should be used if you can get away with it from a security point of view.

 - Elastic load balancer
	 - A good idea if you're using EC2 rather than hosting your own load balancer
	 - Cheapest to start with
		 - you pay for what you use and there is no cost for setting up an ELB instance
	 - Scales transparently so the load balancer is never the bottleneck
		 - has high availability
		 - integrates with autoscaling of EC2 instances so they can be replaced in case of web server failures
	 - Can perform SSL termination
	 - It needs time to warmup and scale out, it can't handle a burst of traffic that requires doubling capacity in a matter of seconds.

 - open source software based load balancers
	 - Nginx - can also act as a reverse HTTP proxy so it can cache http responses from your servers, making it suitable as an internal web service load balancer.
	 - HAProxy - is just a load balancer.
		 - can be setup to not inspect higher level protocols and depend entirely on tcp/ip headers to distribute the traffic, meaning it can be a load balancer for any protocol, not just http or https
			 - can distribute services like cache servers, message queues and databases
			 - performs slightly faster than nginx
		 - layer 7 proxy which supports sticky sessions and ssl termination but needs more resources to track http specific info
	 - Have to manually scale the load balancer yourself