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

A load balancer accepts incoming traffic from clients and routes requests to its registered targets (such as EC2 instances) in one or more Availability Zones. The load balancer also monitors the health of its registered targets and ensures that it routes traffic only to healthy targets. When the load balancer detects an unhealthy target, it stops routing traffic to that target. It then resumes routing traffic to that target when it detects that the target is healthy again.

You configure your load balancer to accept incoming traffic by specifying one or more listeners. A listener is a process that checks for connection requests. It is configured with a protocol and port number for connections from clients to the load balancer. Likewise, it is configured with a protocol and port number for connections from the load balancer to the targets.

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


