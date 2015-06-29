# Ansible

Requirements on hosts:

 * SSH
 * Python 2.5 or later

Control machine requires Python 2.6 or later.

Ansible is push-based, i.e. updates occur only when a playbook is run. However, pull-based support is available via `ansible-pull`.

No abstraction is available, so playbooks are OS and distribution specific (e.g. use `apt` for Debian).

Ansible runs each task in parallel across every host, and does not move on to the next task until all hosts have completed.
