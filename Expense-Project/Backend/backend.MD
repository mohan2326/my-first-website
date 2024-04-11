### Backend
Backend service is responsible for adding the given values to database. Backend service is written in NodeJS, Hence we need to install NodeJS.

**Developer has chosen NodeJs, Check with developer which version of NodeJS is needed. Developer has set a context that it can work with NodeJS >20**

Install NodeJS, By default NodeJS 16 is available, We would like to enable 20 version and install this.

**You can list modules by using dnf module list**

```
dnf module list
```

```
dnf module disable nodejs:18 -y
```
```
dnf module enable nodejs:20 -y
```

```
dnf install nodejs -y
```

Configure the application.

Add application User
```
useradd expense
```

User expense is a function / daemon user to run the application. Apart from that we don't use this user to login to server.

Also, username expense has been picked because it more suits to our project name.

We keep application in one standard location. This is a usual practice that runs in the organization.

Lets go to an app directory.

```
cd /app
```
Every application is developed by development team will have some common softwares that they use as libraries. This application also have the same way of defined dependencies in the application configuration.

Lets download the dependencies.

```
npm install
```

We need to setup a new service in systemd so systemctl can manage this service

Setup SystemD Expense Backend Service
```
vim /etc/systemd/system/backend.service
```

```
[Unit]
Description = Backend Service

[Service]
User=expense
Environment=DB_HOST="<MYSQL-SERVER-PRIVATE-IPADDRESS>"
ExecStart=/bin/node /app/index.js
SyslogIdentifier=backend

[Install]
WantedBy=multi-user.target
```

**NOTE: Ensure you replace <MYSQL-SERVER-IPADDRESS> with IP address**

Load the service.

```
systemctl daemon-reload
```

Start the service.
```
systemctl start backend
```
```
systemctl enable backend
```

For this application to work fully functional we need to load schema to the Database.

We need to load the schema. To load schema we need to install mysql client.

To have it installed we can use
Install MySQL Server 8.0.x

```
dnf install mysql-server -y
```

Start MySQL Service

```
systemctl enable mysqld
```
```
systemctl start mysqld
```
Load Schema

```
mysql -h <MYSQL-SERVER-IPADDRESS> -uroot -p(password you have set in the backend service)
```