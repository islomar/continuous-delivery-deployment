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
  * http://12factor.net/ The twelve-factor app is a methodology for building software-as-a-service apps that:
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
www.terraform.io
Permite declarar recursos.
Create www.tf (hay que meter claves)
> terraform plan
> terraform apply
> terraform show

* Foreman para Ruby


## Deployment pipeline
* Video 1 = ### Configuration management 5

Sessión de dudas Continuous Delivery:
https://www.youtube.com/watch?v=3sEVv7hgkvk


## Gestión de infrastructuras y entornos 1
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


## Gestión de infrastructuras y entornos 2
* Create a playbook to replicate the steps in "My first 5 minutes on a server".
* The password in playbook must be the result from: mkpasswd -m sha-k512
* I created a new id_rsa_ansible.pub:
  * ssh-keygen -t rsa
  * ssh-add ~/.ssh/id_rsa_ansible

Bookmark: 

##Questions:
* The example of "My first 5 minutes on a server" always executes the "disable ssh root login" task, why??

##Pending to be read
* 12factor
* Otto
* Terraform

##Interesting links
* Securing Debian: https://www.debian.org/doc/manuals/securing-debian-howto/securing-debian-howto.en.pdf
* My first 5 minutes on a server: http://plusbryan.com/my-first-5-minutes-on-a-server-or-essential-security-for-linux-servers