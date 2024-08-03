# Table of Contents
1. [What is Elastic Load Balancer](#What-is-load-balancer)
2. [Service can be used in ELB](#services-can-be-used-in-elb)
3. [How Elastic Load Balancing works](#How-Elastic-Load-Balancing-works)

## What is Load Balancer
Elastic Load Balancing automatically distributes your incoming traffic across multiple targets, such as EC2 instances, containers, and IP addresses, in one or more Availability Zones. It monitors the health of its registered targets, and routes traffic only to the healthy targets.

## Service can be used in ELB

- EC2

    Virtual servers that run your applications in the cloud. You can configure your load balancer to route traffic to your EC2 instances
- Amazon EC2 Auto Scaling

    Ensures that you are running your desired number of instances, even if an instance fails. Amazon EC2 Auto Scaling also enables you to automatically increase or decrease the number of instances as the demand on your instances changes
- AWS Certificate Manager

    When you create an HTTPS listener, you can specify certificates provided by ACM. The load balancer uses certificates to terminate connections and decrypt requests from clients.
- Amazon CloudWatch

    Enables you to monitor your load balancer and to take action as needed
- Amazon ECS

    Enables you to run, stop, and manage Docker containers on a cluster of EC2 instances. You can configure your load balancer to route traffic to your containers
- AWS Global Accelerator

    Improves the availability and performance of your application. Use an accelerator to distribute traffic across multiple load balancers in one or more AWS Regions
- Route 53

    Provides a reliable and cost-effective way to route visitors to websites by translating domain names into the numeric IP addresses that computers use to connect to each other.For example, it would translate www.example.com into the numeric IP address 192.0.2.1. AWS assigns URLs to your resources, such as load balancers. However, you might want a URL that is easy for users to remembe
- AWS WAF

    You can use AWS WAF with your Application Load Balancer to allow or block requests based on the rules in a web access control list (web ACL)

## How ELB works
When we create a loadbalancer, it creates a load balancer node in each AZ.When a load balancer receives a request, it sends it to the load balancer node and that load balancer node route that request to the registered targets.

A load balancer accepts incoming traffic from clients, and routes requests to its registered targets (such as EC2 instances) in one or more Availability Zones. The load balancer also monitors the health of its registered targets and ensures that it routes traffic only to healthy targets. When the load balancer detects an unhealthy target, it stops routing traffic to that target. It then resumes routing traffic to that target when it detects that the target is healthy again.

### Listners
You configure your load balancer to accept incoming traffic by specifying one or more listeners. A listener is a process that checks for connection requests. It is configured with a protocol and port number for connections from clients to the load balancer ( called frontend-connection ). Likewise, it is configured with a protocol and port number for connections from the load balancer to the targets (called backend-connection).

## Types of LB
- Application Load Balancers
- Network Load Balancers
- Gateway Load Balancers
- Classic Load Balancers

## Availability Zones and load balancer nodes

When you enable an Availability Zone for your load balancer, Elastic Load Balancing creates a load balancer node in the Availability Zone. If you register targets in an Availability Zone but do not enable the Availability Zone, these registered targets do not receive traffic. Your load balancer is most effective when you ensure that each enabled Availability Zone has at least one registered target.

We recommend enabling multiple Availability Zones for all load balancers. With an Application Load Balancer however, it is a requirement that you enable at least two or more Availability Zones. This configuration helps ensure that the load balancer can continue to route traffic. If one Availability Zone becomes unavailable or has no healthy targets, the load balancer can route traffic to the healthy targets in another Availability Zone.

After you disable an Availability Zone, the targets in that Availability Zone remain registered with the load balancer. However, even though they remain registered, the load balancer does not route traffic to them.

## Cross-zone loadbalancing

- When cross-zone load balancing is enabled, each load balancer node distributes traffic across the registered targets in all enabled Availability Zones
- When cross-zone load balancing is disabled, each load balancer node distributes traffic only across the registered targets in its Availability Zone


## Routing algorithm

With Application Load Balancers, the load balancer node that receives the request uses the following process:

- Evaluates the listener rules in priority order to determine which rule to apply.

- Selects a target from the target group for the rule action, using the routing algorithm configured for the target group. The default routing algorithm is round robin. Routing is performed independently for each target group, even when a target is registered with multiple target groups.

## HTTP Requests

When client has to send or retrive the data to the server or from the server, it first establish a connection which is TCP. Once connection is established, client send or retrive the data from the server using that connection/link

There are multiple versions of http
1. http/0.9
    - The earliest version of HTTP, primarily used for serving HTML pages.
    - Only supported the GET method
    - No provision for headers or metadata in requests and responses
    - Each request required a new TCP connection.
2. http/1.0
    - One request per connection
    - Allowed serving of different content types (images, files, etc.)

### HTTP requests in ELBs

- Clasic and ALB uses the multiplexing. This means that requests from multiple clients on multiple front-end connections ( client to load balancer ) can be routed to a given target through a single backend connection ( load balancer to target ).
- Connection multiplexing improves latency and reduces the load on your applications
- To prevent connection multiplexing, disable HTTP keep-alive headers by setting the Connection: close header in your HTTP responses

## HTTP headers

Application Load Balancers and Classic Load Balancers automatically add X-Forwarded-For, X-Forwarded-Proto, and X-Forwarded-Port headers to the request.

## Load balancer scheme

When you create a load balancer, you must choose whether to make it an internal load balancer or an internet-facing load balancer.

### Internet facing load balancer
The nodes of an internet-facing load balancer have public IP addresses. The DNS name of an internet-facing load balancer is publicly resolvable to the public IP addresses of the nodes. Therefore, internet-facing load balancers can route requests from clients over the internet.

### Internal load balancer
The nodes of an internal load balancer have only private IP addresses. The DNS name of an internal load balancer is publicly resolvable to the private IP addresses of the nodes. Therefore, internal load balancers can only route requests from clients with access to the VPC for the load balancer.

- Both internet-facing and internal load balancers route requests to your targets using private IP addresses.
- Ideal scenerio is, register web servers into the internet facing loadbalancer and application servers into the internal-facing loadbalancers. 

## Network MTU 

The maximum transmission unit (MTU) determines the size, in bytes, for the largest packet that can be sent over the network. The larger the MTU of a connection, the more data that can be passed in a single packet.

The MTU size on load balancer nodes is not configurable. Jumbo frames (9001 MTU) are standard across load balancer nodes for Application Load Balancers, Network Load Balancers, and Classic Load Balancers.