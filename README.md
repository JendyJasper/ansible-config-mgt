# RUNNING ANSIBLE PLAYBOOK FROM JENKINS
- Installing Ansible on Jenkins
- Installing Ansible plugin in Jenkins UI
- Creating Jenkinsfile from scratch.
- - Note: Ensure that Ansible runs against the Dev environment successfully.
 
Tutorial to guide through the step: 
  -  https://www.youtube.com/watch?v=PRpEbFZi7nI

Tutorial on configuring nginx and php on RHEL/CENTOS server: 
  -  https://www.linuxhelp.com/how-to-test-the-php-configuration-on-apache-and-nginx-web-servers-in-centos-7-6
  -  https://www.youtube.com/watch?v=gd1y6vFGW9w&t=2

Tutorial to install php 7.4
  -  https://computingforgeeks.com/how-to-install-php-7-4-on-centos-rhel-8/

Commands to dynamically set hostname, domain name and IP address to config files:
  -  server_IP {{ ip_address }};
  -  domain: {{ ansible_nodename }}
  -  hostname: {{ansible_default_ipv4.address}}

Tutorial to redirect www or http to non www and https and vice versa
  -  https://phoenixnap.com/kb/redirect-http-to-https-nginx

Tutorial to set up let's encrypt on Ubuntu with auto cert renewal
  -  https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-20-04

Tutorial to set up let's encrypt / certbot on Rhel server
  -  https://www.cyberithub.com/how-to-install-lets-encrypt-certbot-on-rhel-centos-8/

Tutorial to configure nginx as gateway for multiple servers
  -  https://www.technhit.in/configure-nginx-as-gateway-for-multiple-servers/
  > Note: Only the IP address of the reverse proxy server will be added to the DNS A record of the domain. The rest of the work happens inside the proxy server. Remember to update your hosts file to include the public IP address of the servers and their domains.

Tutorial to Install Apache, MySQL, PHP (LAMP) on CentOS/RHEL 7
  -  https://tecadmin.net/install-lamp-apache-mysql-and-php-on-centos-rhel-7/
  >  Remember that php-mysql is for ubuntu while php-mysqlnd is for redhat. Also, when you encounter an error, always try to read the log files of the server to get the actuall reason for the error. The file is usually in /var/log/nginx/error.log.

Tutorial on fixing proxy 502 bad gateway error rhel and maybe ubuntu. Also consider using public IP address for the proxy_pass if private IP still gives the connection to upstream refused error.
  -  https://stackoverflow.com/questions/49597942/load-balancer-on-nginx-give-502-bad-gateway
  -  https://stackoverflow.com/questions/23948527/13-permission-denied-while-connecting-to-upstreamnginx
  -  https://stackoverflow.com/questions/70111791/nginx-13-permission-denied-while-connecting-to-upstream
  -  https://serverfault.com/questions/819423/reverse-proxy-nginx-bad-gateway

Tutorial to enable your server to connect to a database over HTTP(Especially for RHEL server)
  -  https://stackoverflow.com/questions/41178774/connect-database-error-type-2002-permission-denied

Tutorial to print the actual database connection error which should help during debugging
  -  https://www.plus2net.com/php_tutorial/mysqli_connection.php

Tutorial to access the environment variables of the machine which ansible is running from / and also to access the Jenkins environment variables if you are runnimg ansible from jenkins
  - https://docs.ansible.com/ansible/latest/collections/ansible/builtin/env_lookup.html#examples
  - https://github.com/jenkinsci/ansible-plugin/blob/main/README.md
  - https://wiki.jenkins.io/display/JENKINS/Building+a+software+project

    - examples code:
    ```
    ---
    - hosts: test
      name: print workspace
      tasks:
        - name: get workspace
          debug:
            msg: "'{{ lookup('ansible.builtin.env', 'WORKSPACE')}}' is the workspace environment variable"
    ```