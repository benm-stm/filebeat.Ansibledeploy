filebeat deploy
=========

this role allows the deployment of a filebeat in a machine debian or rhel based it can also :
- install dynamic filbeat conf file defined in the templates
- deploy conf, lib, logs of filebeat using la poste standard
- install filebeat via an existing filebeat rpm/deb in files, if not try to download the specified version from elastic repo and install it

Requirements
------------

in order to run you have to install these tools in your host machines :

- nohup
- yum/rpm (if rhel), apt (if debian)

Role Variables
--------------

Host vars (specific to each platform):

```
plateform_dir= '/i7h/i7hadmaa'
```

Default variables :

```
filebeat:
  #for rpm based systems
  rhel:
    url: "{{filebeat_rhel_url | default('https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-5.4.2-x86_64.rpm') }}"
    package_name: "{{ filebeat_rhel_package_name | default('filebeat-5.4.2-x86_64.rpm') }}"
  #for apt based system
  deb:
    url: "{{filebeat_deb_url | default('https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-5.4.2-amd64.deb') }}"
    package_name: "{{ filebeat_deb_package_name | default('filebeat-5.4.2-amd64.deb') }}"

#proxy settings
proxy_env: "{{ http_proxy | default('221.128.58.183:3128') }}"
```
Dependencies
------------

NA

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - filebeat

how to run :
```
cd tests/
ansible-playbook -i inventory test.yml
```

there 3 tags available now status, start and stop for filebeat in all the machines, to use it you have to use the syntax below
```
cd tests/
ansible-playbook -i inventory test.yml --tags stop
```
License
-------

BSD

Author Information
------------------

BEN MANSOUR Mohamed Rafik <benmansour_rafik@yahoo.fr>
