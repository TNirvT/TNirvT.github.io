---
layout: post
title: "Shoplist Database"
author: "Terry"
categories: blog
tags: []
image: cover-06.jpg
---

# Database design

In the Password manager project, the database design is rather basic and size will be limited, only contains one table to store the url, encrypted password, login and optional note. However the Shoplist database requires tables to store user login data, item data, prce history, etc. MySQL relational database is used this time. After all, Password manager was designed for one user only, but Shoplist is for more users.  
During development, MySQL workbench is very handy to monitor the database.  

[![MySQL workbench Screenshot][img link]][workbench link]  

# Back end coding

Flask works well with SQLAlchemy library that helps manage database, but this time I wanted to get familiar with SQL commands and design on a more fundamental level, I decided to code without the help of an extra library. However it wasn't without any issues. The connection timeout is worth mention, as it seems not appear when using library (such as SQLAlchemy). A common approach is to ping the database server, and reconnect if the connection is lost. Also need to make sure ICMP communication is allowed, between the Python/Flask server and MySQL server. Which, also lead me to learn more about AWS server config, as I setup a MySQL server on AWS using RDS.  

[Github Repository][repo link]  


[repo link]: https://github.com/TNirvT/Shoplist
[img link]: https://drive.google.com/uc?export=view&id=1YKVw6VRiye_N3Tec3xT3xbhtUg5jFFzU "MySQL workbench Screenshot"
[workbench link]: https://www.mysql.com/products/workbench/
