# ansible-pull-example
ansible-pull example

# About

This is an example of how to set up deployments using `ansible-pull`. This sets up `ansible-pull` to run at a scheduled frequency, using the example deployment in `playbook.yml`. This being ansible, you are of course not limited to using it purely for docker deployments.

# Setup

Install Dependencies:

```
sudo apt install python3
sudo apt install python3-pip
sudo pip3 install ansible
```

Install using the `ansible_pull_command` in `initial_setup_playbook.md`:

```
/usr/local/bin/ansible-pull \
--directory /var/ansible-deployments \
--checkout master \
--url git://github.com/cyrusroshan/ansible-pull-example \
playbook.yml
```

## Post-installation:

To look at logs, use `journalctl`:

```
journalctl -xe --since "-10m" -u ansible-deployments.service
```