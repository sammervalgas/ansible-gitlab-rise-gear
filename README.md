Ansible Gitlab Rise Gear (Centos)
=================
Ansible role gitlab automation to create groups, subgroups and projects

Requirements
----------------
* Docker
* Ansible >=2.8

Environment (localhost)
----------------

Run a gitlab-ce docker sample:
```bash
docker pull gitlab/gitlab-ce:latest

docker run --detach \
--hostname gitlab.example.com \
--publish 443:443 \
--publish 80:80   \
--publish 2222:22 \
--name gitlab     \
--restart always  \
--volume /srv/gitlab/config:/etc/gitlab    \
--volume /srv/gitlab/logs:/var/log/gitlab  \
--volume /srv/gitlab/data:/var/opt/gitlab  \
gitlab/gitlab-ce:latest

# Configure gitlab hostname docker into /etc/hosts
sudo /bin/bash -c 'echo -e "127.0.0.1\ \t gitlab.example.com" >> /etc/hosts'

```
Variables
--------------------

* All variables are set within the file provision with vars_prompt.

```yaml
# Credentials
access_login: GITLAB_TOKEN_LOGIN_OR_USER
access_token: GITLAB_TOKEN_OR_PASS
# Project Setup
group_name: GROUP_NAME_HERE
subgroup: SUBGROUP_NAME_HERE
inner_subgroup: INNER_SUBGROUP_NAME_HERE
inner_subgroup2: INNER_SUBGROUP_NAME_HERE
project: GITLAB_PROJECT_NAME
project_type: app (java_microservices)/ web(angular_node)/ dep(dependencies_only)
gitlab_url: GITLAB_URL_HERE
```

* Change [hosts](hosts) file with your machine access types

```yaml
[localhost:vars]
ansible_user=CHANGE_ME
ansible_pass=CHANGE_ME
ansible_become_pass=CHANGE_ME
ansible_port=22
ansible_connection=local
ansible_host=127.0.0.1

[localhost]
127.0.0.1
```


Example
---------------------

Run the playbook:

```bash
git clone https://github.com/sammervalgas/ansible-gitlab-rise-gear.git
cd ansible-gitlab-rise-gear
ansible-playbook -i hosts provision.yaml
```

Author
---------------------
Sammer Valgas - XGH Expert

License
---------------------
[MIT]()
