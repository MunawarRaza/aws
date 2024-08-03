# Table of Contents
1. [What is Route Table](#What-is-route-table)

## What is Route Table

Route table is a table, in which rules/routes are defined. e.g what to do if traffic comming from a subnet, where to route etc.

All the subnets within a VPC can communicate with each other, because in all the route tables, associated with subnets, a rule is defined which is CIDR of VPC.

Example of private route table
```
Destination     Target
10.0.0.0/16     local
```

If we have to make it public we have to add another rule which is like
Example of public route table
```
Destination         Target
10.0.0.0/16         local
0.0.0.0/0           ig-id
```
- If there are more then one private subnets, attach them with a single routetable
- If there are more than one public subnets, attach them with a public route table




## How to Create subnet
    Name
    Availability Zones
    VPC
    CIDR Block


