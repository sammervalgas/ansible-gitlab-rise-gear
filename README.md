Ansible gitlab rise gear (Centos)
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

All variables are set within the file provision

```yaml
access_token: GITLAB_TOKEN_HERE
group_name: GROUP_NAME_HERE
subgroup: SUBGROUP_NAME_HERE
inner_subgroup: INNER_SUBGROUP_NAME_HERE
inner_subgroup2: INNER_SUBGROUP_NAME_HERE
project: GITLAB_PROJECT_NAME
gitlab_url: GITLAB_URL_HERE
```

Example
---------------------

Run the playbook:

```bash
git clone https://github.com/sammervalgas/ansible-gitlab-rise-gear.git
cd ansible-gitlab-rise-gear
ansible-playbook provision.yaml
```
> :warning: Note: My hosts configurarions are inside ansible.cfg

Author
---------------------
Sammer Valgas - XGH Expert

License
---------------------
[MIT]()
