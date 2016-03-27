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

##Pending to be read
* 12factor
* Otto
* Terraform

##Interesting links
* Securing Debian: https://www.debian.org/doc/manuals/securing-debian-howto/securing-debian-howto.en.pdf