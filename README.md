# ansible_install_multiple_pkg
This is sample installation for multiple packages using ansible


# code
```
---
  - name: "Deploying multiple pkg"
    hosts: all
    become: yes
    tasks:
      - name: "installing Apache, PHP and MariaDB"
        yum:
          name:
            - httpd
            - php
            - mariadb-server
          state: present
      - name: "starting service"
        service:
          name: httpd,mariadb
          state: restarted
          enabled: yes
      - name: "Host a file"
        copy:
          content: "Hello World Multiple"
          dest: /var/www/html/index.html
          owner: apache
          group: apache
```
