This is a 0x1A. Application server readme file.

Concepts
For this project, we expect you to look at these concepts:

Web Server
Server
Web stack debugging

Background Context
Your web infrastructure is already serving web pages via Nginx that you installed in your first web stack project. While a web server can also serve dynamic content, this task is usually given to an application server. In this project you will add this piece to your infrastructure, plug it to your Nginx and make is serve your Airbnb clone project.

Application server vs web server
How to Serve a Flask Application with Gunicorn and Nginx on Ubuntu 16.04 (As mentioned in the video, do not install Gunicorn using virtualenv, just install everything globally)

Running Gunicorn
Be careful with the way Flask manages slash in route - strict_slashes

Upstart documentation

TASKS
2	2-app_server-nginx_config	
3	3-app_server-nginx_config	
4	4-app_server-nginx_config	
5	5-app_server-nginx_config	
6	gunicorn.service	
7	4-reload_gunicorn_no_downtime
