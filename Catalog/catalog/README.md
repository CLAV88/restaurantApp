# Restaurant Menus Application - Final Project (Udacity)

## Brief Description

Final Project for Udacity Full Stack Web Development Course.

The goal was to create a working Auth2.0 web application using modern frameworks in a custom configured server in the cloud on AWS.

This is a full CRUD capable application, to demonstrate understanding of how using the Python Flask Framework & WSGI hosted on custom configured Ubuntu instance in the cloud on AWS on a custom configured instance of a server (Ubuntu 18.04) on AWS lightsail.

The application has multiple easy to use API endpoints to expose the data in the PSQL database underlying the site, and allows any user with a Google account to create custom lists of restaurants (along with menus, prices, food characteristics) all on their own.

## Running the Restaurant Menu App
Once it is up and running, type **ssh grader@35.183.175.71 -i /c/Users/calvi/.ssh/LightSailNew.pem**. This will log your terminal into the virtual machine on AWS so long as you have the correct pub key and password, When you want to log out, type **exit** at the shell prompt.  To turn the virtual machine off (without deleting anything), type **vagrant halt**. If you do this, you'll need to run **vagrant up** again before you can log into it.


Now that you have Vagrant up and running type **vagrant ssh** to log into your VM.  change to the /vagrant directory by typing **cd /vagrant**. This will take you to the shared folder between your virtual machine and host machine.

Type **ls** to ensure that you are inside the directory that contains project.py, database_setup.py, and two directories named 'templates' and 'static'

Now type **python database_setup.py** to initialize the database.

Type **python lotsofmenus.py** to populate the database with restaurants and menu items. (Optional)


## Here's the real website, Check it out!
![Restaraunt App Website Homepage](/Catalog/catalog/static/RestaurantApp.JPG)
(<http://35.183.175.71.xip.io)>

## Instructions for upping venv for python 2.7 within server to make any needed changes to the packages that the python instance on the VM uses to run the app.

> source venv/bin/activate

## Dependencies

### (Python 2.7 libs) in the VM now

Package         Version
--------------- ---------

1. certifi         2019.6.16
2. chardet         3.0.4
3. Click           7.0
4. Flask           1.0.3
5. Flask-SeaSurf   0.2.2
6. httplib2        0.13.0
7. idna            2.8
8. itsdangerous    1.1.0
9. Jinja2          2.10.1
10. MarkupSafe      1.1.1
11. oauth2client    4.1.3
12. pip             19.1.1
13. psycopg2-binary 2.8.3
14. pyasn1          0.4.5
15. pyasn1-modules  0.2.5
16. requests        2.22.0
17. rsa             4.0
18. setuptools      41.0.1
19. six             1.12.0
20. SQLAlchemy      1.3.5
21. urllib3         1.25.3
22. Werkzeug        0.15.4
23. wheel           0.33.4

### Git

If you don't already have Git installed, [download Git from git-scm.com.](http://git-scm.com/downloads) Install the version for your operating system.

On Windows, Git will provide you with a Unix-style terminal and shell (Git Bash).  
(On Mac or Linux systems you can use the regular terminal program.)

You will need Git to install the configuration for the VM. If you'd like to learn more about Git, [take a look at our course about Git and Github](http://www.udacity.com/course/ud775).



