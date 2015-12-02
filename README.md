Spitter
=======

Introduction
------------

This project imitates the fundamental features of Twitter. It is based on 3 layer architecture. Presentation layer is carried out in Spring MVC, Tiles2, and JavaScript. Service and Persistence layers use core Spring functionality leveraged by Hibernate. The entire project is built in Maven and current connection settings use PostgreSQL database.

Of course this is not how real Twitter application works. Using traditional database for their purpose is completely unfeasible.

The project was inspired by "Spring in Action" book, by C. Walls.

![spitter](https://raw.githubusercontent.com/djangofan/spitter/master/spitter.png)

Project Features
-------------

The application enables to register a new account or sign in using existing one. Each registered user can navigate the application through the dashboard where he can post a new message (visible to all who follow him), search for other people, follow and unfollow other users. The user has full control over his own posts and can delete them at any time, as well as customize his own profile (including providing personal information and uploading avatar).

#### List of features (ROLE_USER):

1. Register new account
2. Remind password on email
3. Customize the profile (personal details, upload/remove picture)
4. Post message which would be visible to the user and people who follow him/her
5. Delete his/her messages
6. Search for other users and browse their profiles
7. Follow/Unfollow other users (link in their profile)
8. Browse list of followers/following

#### List of features (ROLE_ADMIN):

1. Everything and standard user
2. Access to admin panel (restricted for other users)
3. Browse list of all users, or by specified query
4. Delete particular user

#### Known issues
See this URL for known issues that need to be fixed:
https://github.com/djangofan/spitter/issues

Quick Start Guide
-----------------

Before you deploy this project on the server (if you're using Eclipse make sure to "Maven>Update project" beforehand):

``tomcat:run``

make sure to provide your own details regarding database connection and email used as a reminder (my implementation facilitates GMail).

In spring-servlet.xml, lines 32 and 33 -- make sure to provide username and password to your email account:

```xml
<property name="username" value="spitter.reminder" />
<property name="password" value="yourPass" />
```

In spring-servlet.xml, line 74 provide the path to your database (you can name it whatever you want):

```xml
<property name="url" value="jdbc:postgresql://localhost:5432/spitter_db"></property>
```

and in line 76 provide your password:

```xml
<property name="password" value="yourPass" />
```

To enable using HTTPS, adjust your server in spring-security.xml in lines 10, 11, and 12 to add XML attribute:

``requires-channel="https"``

After signing yourself up initially, you'll need to change yourself as a ROLE_ADMIN by editing the spitter_db.spittr.grantedauthority field.   Then, you will be able to access the admin at:

``http://localhost:8080/spitter/admin/main``


