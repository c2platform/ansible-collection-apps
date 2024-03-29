# Ansible Role c2platform.apps.guacamole

An Ansible Role that installs [Guacamole](https://guacamole.apache.org/) using Docker images [guacamole/guacamole](https://hub.docker.com/r/guacamole/guacamole) and [guacamole/guacd](https://hub.docker.com/r/guacamole/guacd). These images are created using GitHub projects [apache/guacamole-client](https://github.com/apache/guacamole-client) and [apache/guacamole-server](https://github.com/apache/guacamole-server) respectively. See also [Apache Guacamole™](https://guacamole.apache.org/)

<!-- MarkdownTOC levels="2,3" autolink="true" -->

- [Requirements](#requirements)
- [Role Variables](#role-variables)
- [Dependencies](#dependencies)
- [Example Playbook](#example-playbook)

<!-- /MarkdownTOC -->

## Requirements

<!-- Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required. -->

PIP package **docker** is required which you can install using list `common_pip_packages_extra`

```yaml
common_pip_packages_extra:
  - docker
```

## Role Variables

<!--  A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well. -->


```yaml
java_version: openjdk-8-jdk
java_versions:
  openjdk-8-jdk:
    package: yes
    folder: java-8-openjdk-amd64
    keystore: jre/lib/security/cacerts
    trusts: 
      - alias: isrgrootx1
        url: https://letsencrypt.org/certs/isrgrootx1.pem

guacamole_web_docker_volumes:
  - /etc/ssl/certs/java/cacerts:/usr/local/openjdk-8/jre/lib/security/cacerts
```

## Dependencies

<!--   A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles. -->



## Example Playbook

<!--   Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too: -->

```yaml
    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }
```





