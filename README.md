# zabbix_docker_template
zabbix_docker_template
Zabbix 5.x docker template for Zabbix Agent ver.1, with containers and images LLD

_This should be able to run on older versions of Zabbix too, at least all the functionality required by the template is there on v4.x, but it is only tested on 5.0. 
I was notified of at least one failed attempt to import the template on v4.4.10, probably due to incompatibility of the XML format exported by v5.0_

This doesn't use any external scripts or modules to collect data, the only dependencies are `curl` and read access to docker's API.

*Intended setup:* Running Zabbix Agent alongside Docker on the same host, access API by UNIX socket.

*Possible:* Run Zabbix Agent separately and point the template to docker host, access API by HTTP.

## Setup
- `cp docker_template.conf /etc/zabbix/zabbix_agentd.d/`
- `sudo usermod -a -G docker zabbix`
- restart Zabbix Agent
- import `docker_template_agent1.xml` into Zabbix templates
    
    This will create a template named **Template App Docker - Agent 1**

- attach the new template to hosts to start monitoring
- configure macros as needed
