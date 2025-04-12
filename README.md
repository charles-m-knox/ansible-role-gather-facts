# gather-facts

Gathers facts. Nothing special.

## Requirements

There are no requirements for this, it should work out of the box with Ansible.

## Role Variables

None currently.

## Dependencies

<!-- A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles. -->

None.

## Usage

First, create a `requirements.yml` in your Ansible setup if you haven't already, here's an example:

```yaml
---
collections:
  - name: community.general
  - name: ansible.posix
  - name: community.crypto

roles:
  - name: charles-m-knox.gather-facts
    src: https://github.com/charles-m-knox/ansible-role-gather-facts.git
    scm: git
    version: main
```

Next, install it:

```bash
# include the -f flag to forceably re-install and get the latest (equivalent to
# upgrading)
ansible-galaxy role install -f -r requirements.yml
```

Now, in your `site.yml` (or whatever your playbook is named), use the role:

```yaml
- name: gather facts
  hosts: all
  gather_facts: False
  # helps with gathering facts from slow systems like openwrt
  gather_timeout: 120
  module_defaults:
    ansible.legacy.setup:
      gather_timeout: "120"
    ansible.builtin.gather_facts:
      gather_timeout: "120"
  roles:
    - charles-m-knox.gather-facts
  tags:
    - gather-facts
```

<!-- ## Testing

```bash
ansible-playbook -i tests/inventory tests/test.yml
``` -->

## License

MIT

## Author Information

<https://charlesmknox.com>
