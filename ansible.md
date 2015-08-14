# Ansible

Requirements on hosts:

 * SSH
 * Python 2.5 or later

Control machine requires Python 2.6 or later.

Ansible is push-based, i.e. updates occur only when a playbook is run. However, pull-based support is available via `ansible-pull`.

No abstraction is available, so playbooks are OS and distribution specific (e.g. use `apt` for Debian).

Ansible runs each task in parallel across every host, and does not move on to the next task until all hosts have completed.

## Configuration file

Ansible will look for an `ansible.cfg` file in the following locations:

 1. Location specified by `ANSIBLE_CONFIG` configuration.
 1. `./ansible.cfg`
 1. `~/.ansible.cfg`
 1. `/etc/ansible/ansible.cfg`

Placing the file in the current directory alongside playbooks is the easiest solution, and keeps everything together.

Sample configuration file:

```
[defaults]
hostfile = hosts
remote_user = vagrant
private_key_file = ~/.vagrant.d/insecure_private_key
host_key_checking = False
```

## Command module

Arbitrary commands can be executed using the command module:

```
ansible hostname -m command -a uptime
```

Passing `-s` runs the command as root, using sudo.

Update packages:

```
ansible hostname -s -m apt -a "update_cache=yes"
```

Install package:

```
ansible hostname -s -m apt -a "name=apache2"
```

Restarting service:

```
ansible hostname -s -m service -a "name=apache2 state=restarted"
```

## Playbooks

Playbooks are YAML files which contain tasks to be run on a group of hosts. Each playbook must contain:

 * A list of hosts.
 * A list of tasks to be run on the hosts.

Command: `ansible-playbook playbook.yml`

The `sudo` option in a playbook means that every task should be run via `sudo`. This is particularly useful on Ubuntu servers, and also on servers where root SSH login has been disabled (as it should be).

## Handlers

Handlers are similar to tasks, but they only run if notified. An example handler might be:

```
handlers:
    - name: restart apache
      service: name=apache2 state=restarted
```

This will run if a task includes:

```
notify: restart apache
```

Handlers run after all tasks, and only run once regardless of how many times they are notified.

## File conventions

 * Support files (e.g. configuration) in: `files`
 * Template files in: `templates`
