---
layout: post
title: "Password Manager development notes"
author: "Terry"
categories: blog
tags: []
image: cover-03.jpg
---

# Start Simple

While learning Python programming, I started building a command line project serves as a basic password manager. Unlock with a master password, enter an url to create a new entry. The program may read url from clipboard too.
With features such as:  
- recognize entry by top-level domain instead of unprocessed url
- passwords are encrypted, and
- saved in SQLite database

The user input url is parsed using [tldextract](https://pypi.org/project/tldextract/), and match if there's any existing record in the database. User is then asked for the corresponding password, or simply hit return key to generate one automatically. The password is then encrypted by [cryptography](https://pypi.org/project/cryptography/)before saved. The database is rather straightforward, contains only one table, that stores all the url(top-level domain only), logins, encrypted passwords and some additional notes. To save a few clicks, when user access a particular entry, e.g. create new entry or change password, the password is copied to clipboard by [pyperclip](https://pypi.org/project/pyperclip/), it works on Windows, MacOS and Linux.  
A small project, yet involves several skills in cipher, string manupilation and database.  

[![Password Manager Screenshot][img link]][repo link]  

[Github Repository of CLI version][repo link]  

## Building a Web Interface

With a web interface the application is more accessible. I started building the web version of the orginal command line Password Manager, using purely Flask at first. Then rewrote the front end using React and Axios afterwards. The application is suppposed to be ran locally though. Eventually, Pytest and Jest were added to run unit tests.  
The web version serves same functions as the command line app, using only minimial style sheet. But in the process, I can get my hands on various libraries to enchance my skills in Flask, Javascript, React, Axios, Pytest and Jest. And also need to review the project in a design aspect.

[![Password Manager Web Screenshot][img link(web)]][repo link(web)]  

[Github Repository of Web version][repo link(web)]  

[repo link]: https://github.com/TNirvT/PasswordManager
[img link]: https://drive.google.com/uc?export=view&id=16P6nUUd0PZ0Od7qE4wf2INMUa6wLGAdD "Password Manager Screenshot"
[repo link(web)]: https://github.com/TNirvT/PasswordManagerWeb
[img link(web)]: https://drive.google.com/uc?export=view&id=19paCaYgjA5q3j-Wwb3ikh4MLNXTKR-eH "Password Manager Web Screenshot"
