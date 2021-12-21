# MidExam_Parman
Midterm EXAM Repository



# START of  LAMP STACK
#LAMP Dependencies <START>
- name: Install LAMP Dependencies (Ubuntu)
  apt:
    name:
      - apache2
      - mariadb-server
      - mariadb-client
      - software-properties-common
- name: PHP Dependencies
  apt:
    pkg:
      - php
      - php-curl
      - php-gd
      - php-mbstring
      - php-xml
      - php-xmlrpc 
      - php-soap 
      - php-intl
      - php-zip
      - php-cli
      - php-mysql
      - php8.0-common
      - php8.0-opache
      - php-gmp
      - php imagick
      - php-gd
      - php-json
      - php-cgi
      - php-gd
      - php-xsl 
    state: latest
    update_cache: true
#LAMP Dependencies <END>

# PHP dependencies <START>
- name Installation software-properties-common
  apt: name=software-properties-common
 
- name: "Repo PHP"
  apt_repository:
    repo="ppa:ondrej/php"

- name: "Updating the repo"
  apt: 
    update_cache=yes

#Enable LAMP services <START>
- name: Run daemon-reload  
  systemd: daemon_reload=yes

- name: Enable service Apache
  systemd:
    name: apache2
    state: started
    enabled: yes

- name: Enable service Mariadb
  systemd:
    name: mariadb
    state: started
    enabled: yes
#Eable LAMP services <END>

# End of LAMP Stack

