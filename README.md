# Dockerized Web Application Setup

This project demonstrates how to set up a web application within a Docker container. It covers exposing the application through port mapping
and the basic steps to get an Apache web server running.

##  Key Concepts

* **Port Exposing:** Docker allows you to map ports between your host machine and the container. This makes the application accessible from outside
*  the container.  For example, you can map port `1234` on your machine to port `80` inside the container where Apache is running.

##  Usage

1.  **Running the Docker Container:**

    To run the container with port mapping, use the following Docker command:

    ```bash
    docker run -it -p 1234:80 --name webapp ubuntu /bin/bash
    ```

    This command does the following:

    * `-it`:  Runs the container in interactive mode with a pseudo-TTY.
    * `-p 1234:80`:  Maps port 1234 on the host to port 80 in the container.
    * `--name webapp`:  Assigns the name "webapp" to the container.
    * `ubuntu /bin/bash`:  Uses the Ubuntu image and starts a Bash shell inside the container[cite: 2].

2.  **Setting up Apache inside the Container:**

    Once inside the container, you can set up your web server.  Here are the steps:

    ```bash
    apt update && apt install apache2 -y
    cd /var/www/html/
    rm index.html
    apt install git -y 
    git clone [https://github.com/your-github-gayathriinanda/Apachewebsite](https://github.com/your-github-gayathriinanda/Apachewebsite) 
    service apache2 start
    ```

    * `apt update && apt install apache2 -y`: Updates the package list and installs Apache2
    * `cd /var/www/html/`: Navigates to the Apache web root directory.
    * `rm index.html`: Removes the default index.html.
    * `git clone https://github.com/your-github-username/your-apache-website`: Clones your website files from a Git repository.
    * `service apache2 start`: Starts the Apache2 server

##  Important Notes

* **Security:** When exposing ports, be mindful of security.  The document mentions that setting security group rules to allow access from known
*  IP addresses is recommended[cite: 5].  Avoid allowing access from `0.0.0.0/0` (all IP addresses) in production environments.
* **AWS EC2 (Example):** The provided document also touches on configuring an AWS EC2 instance.  If you are deploying to AWS, you'll need to
* configure your EC2 security group to allow inbound traffic on the exposed port (e.g., 1234)[cite: 4].

##  Website Access

Once everything is set up, you should be able to access your website using the server's public IP address and the exposed port (e.g., `http://your-public-ip:1234`)
