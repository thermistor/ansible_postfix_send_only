# postfix\_send_only

An ansible galaxy role to install and configure a send-only postfix mail server.

## Requirements

Ubuntu

## Role Variables

* `postmaster_email` the email address for the postmaster of the server.
* `postfix_send_only_hostname` the hostname for sending from

## Example Playbook

    - hosts: servers
      roles:
         - { role: postfix_send_only, postmaster_email: you@example.com  }

## License

Licensed under the MIT License. See the LICENSE file for details.
