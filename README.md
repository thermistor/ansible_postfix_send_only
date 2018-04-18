# postfix\_send_only

An ansible galaxy role to install and configure a send-only postfix mail server.

## Requirements

Ubuntu

## Role Variables

* `postfix_send_only_postmaster_email` the email address for the postmaster of the server.
* `postfix_send_only_hostname` the hostname for sending from

## Example Playbook

    - hosts: servers
      roles:
         - role: thermistor.postfix_send_only
           postfix_send_only_postmaster_email: you@example.com
           postfix_send_only_hostname: example.com

## License

Licensed under the MIT License. See the LICENSE file for details.
