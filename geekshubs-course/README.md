# Continuous Delivery Course

Trainer: Néstor Salceda

Slides:
https://github.com/nestorsalceda/geekshubs-continuous-delivery

Presentation:
http://content.geekshubsacademy.com/courses/GeeksHubsAcademy/CCD-01/2016_T1/about

Content:
http://content.geekshubsacademy.com/courses/GeeksHubsAcademy/CCD-01/2016_T1/courseware/3f0298653d184f0ba36f96a40b9fb6e2/

Chat:
https://noysi.com/a/#/teams/geekshubs/channels/general/chat

Source code:
https://github.com/nestorsalceda/taller-ansible/tree/master/codingstones-operations
https://github.com/nestorsalceda/continuous-delivery


##Configuration management

How to Write a Git Commit Message: 
http://chris.beams.io/posts/git-commit/

Example repo for Python projects:
https://github.com/kennethreitz/samplemod

Structuring your Python project:
http://docs.python-guide.org/en/latest/writing/structure/

### Configuration management 2
  * Example from Redis sourcecode
  * Example "league" in Rails

### Configuration management 3
  * http://12factor.net/: The twelve-factor app is a methodology for building software-as-a-service apps that:
    * Use declarative formats for setup automation, to minimize time and cost for new developers joining the project;
	* Have a clean contract with the underlying operating system, offering maximum portability between execution environments;
	* Are suitable for deployment on modern cloud platforms, obviating the need for servers and systems administration;
	* Minimize divergence between development and production, enabling continuous deployment for maximum agility;
	* And can scale up without significant changes to tooling, architecture, or development practices.
    * Recomiendan guardar la configuración en variables de entorno (aunque solemos estar acostumbrados a que se guarde en ficheros JSON o YAML).

#### Vagrant
* https://github.com/nestorsalceda/vagrant-madrid-devops/blob/master/slides/index.html
* Interfaz de línea de comandos para VirtualBox

**Sucesor de Vagrant: Otto**
https://www.hashicorp.com/blog/otto.html


### Configuration management 4
* www.terraform.io
* Permite declarar recursos.
* Create www.tf (hay que meter claves)
  * `> terraform plan`
  * `> terraform apply`
  * `> terraform show`
* Foreman para Ruby


## Deployment pipeline
* Video 1 = Configuration management 5

Sessión de dudas Continuous Delivery:
https://www.youtube.com/watch?v=3sEVv7hgkvk


## Gestión de infrastructuras y entornos 1
https://storage.googleapis.com/segmento-geek2/deploy/5.%20Gesti%C3%B3n%20de%20infraestructura%20y%20entornos/11ab8108d324279dcbe445699e2543232f.mp4
Snowflake servers: que cada servidor no sea único, como un copo de nieve
http://martinfowler.com/bliki/SnowflakeServer.html

Objetivo: conseguir los Phoenix Servers, un servidor que puedes tirar abajo y reconstruir sin problemas (http://martinfowler.com/bliki/PhoenixServer.html)

Ansible: 
* no necesita un servidor central, como Chef o Puppet.
* los agentes de Puppet y Chef son lentos, y tienes un demonio ejecutándose (Ansible solo necesita SSH)
* Ansible usa YAML, Puppet y Chef tienen sus DSL propios
* Hecho en Python
* Tiene modules: para MySQL, RabbitMQ, etc.

En el Playbook de Ansible, para el módulo apt, puedes decidir state=latest (siempre instalará la última versión) o state=present (la primera vez instala la última versión, pero después ya nunca la actualiza)


### Gestión de infrastructuras y entornos 2
* Create a playbook to replicate the steps in "My first 5 minutes on a server".
* The password in playbook must be the result from: mkpasswd -m sha-k512
* I created a new id_rsa_ansible.pub:
  * ssh-keygen -t rsa
  * ssh-add ~/.ssh/id_rsa_ansible

### Gestión de infrastructuras y entornos 3
* https://github.com/nestorsalceda/taller-ansible/tree/master/codingstones-operations
  * Guidelines: guidelines.md
* Ansible best practices: http://docs.ansible.com/ansible/playbooks_best_practices.html
  * Layout
* Galaxy Ansible (hub for finding, reusing and sharing the best Ansible content): https://galaxy.ansible.com/
* Roles:
  * exim: for sending emails
  * logwatch: envía un informe diario con logs de diversas cuestiones, puedes detectar ataques.
  * munin: monitoring


### Gestión de infrastructuras y entornos 4
Trying Munin


### Gestión de infrastructuras y entornos 5
*Vault: 
  * https://www.hashicorp.com/blog/vault.html
  * Vault gets integrated with Ansible, in order to encode passwords.
  * Ansible + Vault: http://docs.ansible.com/ansible/playbooks_vault.html
* New version of Muning: http://demo.munin-monitoring.org/
* Chaos Monkey


### Gestión de infrastructuras y entornos 6
* Jenkins
  * wget http://mirrors.jenkins-ci.org/war/latest/jenkins.war
  * java -jar jenkins.war
  * http://localhost:8080/
* TravisCI:  muy caro
* CircleCO:  precio más razonable
* Shippable:  https://app.shippable.com/
* Drone.io:  https://drone.io/
* GoCD:  https://www.go.cd/     >> TRY IT!!  

Brian Marick testing quadrants: http://lisacrispin.com/2011/11/08/using-the-agile-testing-quadrants/



##Script de Deploy
###Video 1
https://storage.googleapis.com/segmento-geek2/deploy/6.%20Script%20de%20Deploy/17fbcf8574d43182ab49459f2e0c530413.mp4
* Immutable servers: Docker
  * It uses:
    * See: http://weng-blog.com/uploads/docker/docker-filesystems-multilayer.png
    * LXC (Linux Containers), similar to Solaris zones.
    * UnionFS: used to layer Docker images. As actions are done to a base image, layers are created and documented, such that each layer fully describes how to recreate an action. This strategy enables Docker's lightweight images, as only layer updates need to be propagated (compared to full VMs, for example).
    * cgroups
    * Bootfs: http://collabnix.com/archives/516
  * Process encapsulations.
  * Docker is composed of:
    * Client
    * Daemon
    * Images
* A container is an instance of an image.
* Example with Wordpress: https://hub.docker.com/_/wordpress/

###Video 2
https://storage.googleapis.com/segmento-geek2/deploy/6.%20Script%20de%20Deploy/18b67c137be4fc7c0156d80d59245e68d8.mp4
* Use of Dockerfile
* Image types you can find in hub.docker.com:
  * onbuild
  * slim
* Trying to dockerize the league example

###Video 3
https://storage.googleapis.com/segmento-geek2/deploy/6.%20Script%20de%20Deploy/19ea5cab72d217a88aa8e64c5b3b675f7a.mp4
* Solving problems with the Locale dockerizing Ruby league example.

###Video 4
https://storage.googleapis.com/segmento-geek2/deploy/6.%20Script%20de%20Deploy/20e3318a95f1bb2001fb13f18b46b8fe64.mp4
* Llenamos los entornos con Ansible >> ¿¿??
* Smoke testing: página 118 del libro W Delivery
* Muestra server-expects de Jaime

###Video 5
https://storage.googleapis.com/segmento-geek2/deploy/6.%20Script%20de%20Deploy/21ed7489dc8f33bd093d297227affb1976.mp4
* Using the codingstones-operations
  * Add a new role for the app
  * We will use ansible to install Docker on a jessie
  * Create an Ansible role for installing Docker, translating the steps from: https://docs.docker.com/engine/installation/linux/debian/
  * We can manage Docker from Ansible with http://docs.ansible.com/ansible/docker_module.html
    * Install python-setuptools
    * Install pip
    * Install docker py

###Video 6
https://storage.googleapis.com/segmento-geek2/deploy/6.%20Script%20de%20Deploy/22edfd109e3604191151c2c7b3f4bba22e.mp4
* It configures nginx as reverse proxy, in order to protect the access to the league app.
* It enabled WWW in the firewall
* It configures Docker so that you can not access the app writing the port in the browser: you don't want to allow to access the server directly, but always through the nginx.

##Zero downtime releasing
###Video 1
https://storage.googleapis.com/segmento-geek2/deploy/7.%20Zero%20Downtime%20Releasing/23f6c437c90466c712b33522b722ff6c29.mp4



##Questions:
* When to use Ansible and when Docker?

##Pending to be read
* 12factor
* Otto
* Terraform
* http://collabnix.com/archives/516
* http://weng-blog.com/2015/06/Docker-Overview/

##Interesting links
* Securing Debian: https://www.debian.org/doc/manuals/securing-debian-howto/securing-debian-howto.en.pdf
* My first 5 minutes on a server: http://plusbryan.com/my-first-5-minutes-on-a-server-or-essential-security-for-linux-servers
* Python best practices and examples:
  * https://github.com/kennethreitz/samplemod
  * Repository structure: http://docs.python-guide.org/en/latest/writing/structure/
