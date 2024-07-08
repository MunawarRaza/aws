# Table of Contents
1. [What is VPC](#What-is-vpc)
2. [What are VPC Features](#What-are-vpc-features)

## What is VPC

With Amazon Virtual Private Cloud (Amazon VPC), you can launch AWS resources in a logically isolated virtual network that you've defined. This virtual network closely resembles a traditional network that you'd operate in your own data center

## What are VPC Features
The following features help you configure a VPC to provide the connectivity that your applications need:

#### VPC

A VPC is a virtual network that closely resembles a traditional network that you'd operate in your own data center

#### Subnets
A subnet is a range of IP addresses in your VPC. A subnet must reside in a single Availability Zone.

#### IP Addressing
You can assign IP addresses to your VPCs and subnets

#### Routing
Use route tables to determine where network traffic from your subnet or gateway is directed.

#### Gateways and Endpoints

A gateway connects your VPC to another network. For example, use an internet gateway to connect your VPC to the internet. Use a VPC endpoint to connect to AWS services privately, without the use of an internet gateway or NAT device.

#### Peering Connection

Use a VPC peering connection to route traffic between the resources in two VPCs.

#### Traffic Mirroring
Copy network traffic from network interfaces and send it to security and monitoring appliances for deep packet inspection.

#### Transit gateways
Use a transit gateway, which acts as a central hub, to route traffic between your VPCs, VPN connections, and AWS Direct Connect connections.

#### VPC Flow Logs

A flow log captures information about the IP traffic going to and from network interfaces in your VPC.

#### VPN connections
Connect your VPCs to your on-premises networks using AWS Virtual Private Network (AWS VPN).

## How to Create VPC
    Name
    CIDR Block
    Tenency

