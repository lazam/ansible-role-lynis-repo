Ansible Playbooks: Lynis
============================

The playbooks contains installation, execution and removal of Lynis.

[Lynis](https://cisofy.com/lynis/) security auditing tool on RHEL/CentOS or Debian/Ubuntu servers.


Requirements
------------

None.

Role Variables
--------------

```yml

/defaults/main.yml

lynis_version: 2.2.0
lynis_version_sha256sum: 64fe15be52fa77bce14250867da87e8c262fb0e9229517c4e2d2d5a38223bea4
```
The version and corresponding `sha256sum` of Lynis to install. Latest version and hash can be found on the [Lynis download page](https://cisofy.com/download/lynis/).

```yml
lynis_src_directory: /usr/local/src/
```
The directory to store the `.tar.gz` and Lynis src files.

```yml
lynis_dest_directory: /opt
```
The directory to hold the Lynis installation.

```yml
lynis_log_directory: /var/log/lynis
```
The directory for the Lynis logs. Used by the cron job. By default Lynis will output the report to `stdout` and log to `/var/log/lynis.log` and `/var/log/lynis-report.dat`.

```yml
lynis_cron: yes
lynis_cron_hour: 3
lynis_cron_minute: 30
```
Lynis cron job configuration. The report, report log, and report data are all written to the `lynis_log_directory`.

```yml
/vars/main.yml

var_hosts: all
var_remote_user: ansible
var_become: yes

```

Dependencies
------------

None.



Executing Playbook
-------------------
``` 
git clone https://github.com/retheshnair/ansible-role-lynis-repo

eval $(ssh-agent) ; ssh-add /home/centos/.ssh/mykey.pem

Modified the local file to include the hosts required. 

ansible-playbook -i local ansible-role-lynis-install.yml

```

