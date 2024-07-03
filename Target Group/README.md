# Table of Contents
1. [What is Target Group](#What-is-target-group)


## What is Target Group

## Create Target Group

### Basic Configuration
    1- Chose target type
    2- Give a name
    3- Chose protocol and port
    4- VPC

### Health Checks

    1- Protocol
    2- Path
    3- Healthy Threshold
    4- Unhealthy Threashold
    5- Timeout
    6- Interval
    7- Success codes

Following is the detailed configuration

### Basic configuration
#### Choose a target type
    Instances
    IP address
    lambda function
    ALB
#### Target group name
#### Protocol
    http/tcp/https
    port
#### IP address type
#### VPC 
#### Protocl Version
    http1
    http2
    gPRC

### Health checks
#### Health check protocol
    http
    https
#### Health Check path
    /
    /doc
    /index.html
#### Advance health checks
    health check port
    health check threashold
    unhealthy threshold
    Timeout
    Interval
    Success code

