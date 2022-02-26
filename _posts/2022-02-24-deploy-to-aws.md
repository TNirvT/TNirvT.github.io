---
layout: post
title: "Depoly web application to AWS"
author: "Terry"
categories: blog
tags: []
image: cover-02.jpg
---

# AWS EC2

It's time to put the Shoplist web application on to the internet! I picked the EC2 on Aamazon Web Services. It is the go-to option for many indivials and companies, to host their web site or other web appication. Basic setup includes:  
- Decide the physical location of the service
- Decide the capacity for the machine (virtual private cloud or vpc), e.g. CPU, storage etc.
- Select the operation system, e.g. Ubuntu, Amazon Linux etc.
- Setup the security options (firewall), only allow desired traffics. e.g. port 22 for SSH, port 443 for HTTPS  
Then it's ready to launch. But, before that, download and save the key for SSH connection.  
The initial launch of the vpc instance will take some time. When it's ready, connect to the instance via SSH. Use git to pull/clone the repository to the new server, and of cause, setup Python virtual environment and install the required packages.  
Supervisor is also needed for managing processes, and Nginx is also needed for HTTPS. The Shoplist application itself is launched by Gunicorn, while this process is managed by Supervisor.  

## AWS RDS

Technically the database can be setup on the same EC2 instance, however considering the capacity of the instance is not that great, I use another AWS RDS to host the MySQL database. The basic setup is even simpler than EC2:
- Select the database engine (i.e. MySQL)
- Configure the root user name and password
- Select storage type, e.g. hard disk or SSD, and size
- Decide if public access is necessary
- Setup the security options (firewall), here I need to allow ICMP traffic between the RDS instance and EC2 instance, to keep the connect alive  

As mentioned before, I use MySQL workbench to monitor the database behavior, and do some experiments, which is very handy.  

## Couldflare

Couldflare provides a number of useful services in one place. I can buy domain name, and use it's DNS service allows all traffic goes to Cloudflare with HTTPS connection, and proxied to my EC2 instance's address. And also generate SSL/TLS certificates, which can be installed on Nginx on the EC2 server. So that the connections from client browser to Cloudflare, and from Cloudflare to AWS EC2 are fully protected.  

[Shoplist running on AWS][live link]  

[Shoplist Repository on Github][repo link]  

[live link]: https://www.tnirvt.net/
[repo link]: https://github.com/TNirvT/Shoplist
