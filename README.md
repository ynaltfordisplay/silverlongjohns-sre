# Overview

This is a single playbook to manage the log rotate config for custom-service on the host silverlongjohns-sre.
It demonstrates a basic Ansible setup to do one task and do it well.

# Use

First install ansible, using `uv`

```bash
uv tool install ansible ansible-core
```

Alternatively use the tools directly through `uvx`

```bash
uvx --from ansible ansible-inventory
```

Show the inventory with

```bash
ansible-inventory --list -y
```

Test connectivity itself

```bash
ansible -m ping silverlongjohns-sre
```

Run the playbook itself

```bash
ansible-playbook playbook-logrotate.yml
```

# Configuration

Common config items are in the `ansible.cfg` file with comments documenting them

# Design

This playbook is set up in a minimalistic design, with some clear entry points to expand its capabilities.
It centralizes most of the core pieces of information we are managing in a single playbook file to make edits easier.
However, the log rotate config file is templated to work for multiple services, since that helps colocate the specifics of the log rotation config.
The playbook also uses some templating to help with DRY internally.

The rationale not to separate components, such as variables, is that it's not yet clear how this is going to be scaled in the future.
Instead, we're waiting for that decision to decide how to structure variables in a coherent system.

The log rotate config is minimally designed to the needs of this exercise.
We didn't want to create a devops hairshirt where we must meticulously copy each and every configuration parameter to create a complete wrapping layer.