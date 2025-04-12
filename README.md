# gather-facts

Gathers facts. Nothing special.

## Requirements

There are no requirements for this, it should work out of the box with Ansible.

## Role Variables

None currently.

## Dependencies

<!-- A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles. -->

None.

## Example Playbook

Here's an example, not everything will be necessary for your use case:

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
    - gather-facts
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
