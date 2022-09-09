# Ansible Playbook Template

Template folder structure for Ansible Playbook projects. Thanks to Adrian Novegil for inspiration.


## Folder structure

````
common/                   
   handlers               # common handlers
   vars                   # common vars

group_vars/               # variables to particular groups
host_vars/                # host-specific variables

roles/                    # all ansible roles should be in here
(optional)

log/                      # Ansible execution log
tests/                    # playbook tests

playbook.yml              # main playbook
README.md
requirements.yml          # role dependencies
````

## Usage

Download or clone this repo to get the base of a new project.

```
#SSH
 $ git clone git@github.com:KasperSkytte/ansible-playbook-template.git

#HTTPS
 $ git clone https://github.com/KasperSkytte/ansible-playbook-template.git
```

If you clone the repo, remove the ```.git``` folder, init a new project and then add the ```origin``` to the playbook repository. Create GitHub repo first and use that if you want.

```
 $ rm -rf .git
 $ git init
 $ git add remote origin add [url-to-the-playbook-repo]
```

Edit as required and update the readme specific to your project.

To create new roles you can use the following command in a terminal:

```
 $ ansible-galaxy init roles/newrole
```

This will create a role folder structure for you to use.

If you prefer, you can add the roles of the project in the ```requirements.yml``` file.

Ansible best practices can be read here: http://docs.ansible.com/playbooks_best_practices.html

## Running the playbook

Either run using the wrapper script `run_playbook.bash playbook.yml` to create a virtual env 
and install ansible and ansible-galaxy roles in there automatically first, or manually [install ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) and run:

Install the dependencies:

```
 $ ansible-galaxy install -r requirements.yml -p roles/
```

Execute the Playbook.

```
 $ ansible-playbook playbook.yml -i hosts -u username -k -v
```

## License

GNU General Public License, version 3.
