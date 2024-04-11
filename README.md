# my-first-website

This project is 3-tier application architecture 

A 3-tier application architecture is a modular client-server architecture that consists of a presentation tier, an application tier and a data tier. The data tier stores information, the application tier handles logic and the presentation tier is a graphical user interface (GUI) that communicates with the other two tiers. The three tiers are logical, not physical, and may or may not run on the same physical server

![alt text](image.png)

Web/Frontend tier --> LB,HTML, CSS, JS, Angular Js, reactjs, etc, nodejs --> Nginx/Apache servers --> http servers
API/APP/Backend tier --> Java, .NET,Python, pHp, etc. --> Jboss/weblogic/websphere --> inbuilt servers like tomcat
DB tier MySQL,MSSQL,Oracle, etc. --> MongoDB, Mysql, Kafka, redis

In My Project im also going to connect to my 3-tier application in AWS 

For this we need
1. AWS (3 ec2-instances)
2. Database ec2 instance (install ec2 instance)
3. Backend ec2 instance (NodeJS, can connecting mysql)
4. Frontend ec2 instance (Nginx,Proxy setup need to connect backend instance)
5. Launce website (by entering frontend public ip)