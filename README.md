# postfix\_send_only

An ansible galaxy role to install and configure a send-only postfix mail server.

## Requirements

Ubuntu

## Role Variables

* `postfix_send_only_postmaster_email` the email address for the postmaster of the server.
* `postfix_send_only_hostname` the hostname for sending from

### Relaying through an SMTP provider

By default mail is delivered directly on port 25. AWS blocks outbound port 25 on EC2, so there mail has to be relayed through an SMTP provider such as Mailgun, SES or Postmark.

* `postfix_send_only_relay_host` the provider's SMTP host, e.g. `smtp.mailgun.org`. Empty (the default) delivers directly.
* `postfix_send_only_relay_port` defaults to `587`. TLS is required when relaying.
* `postfix_send_only_relay_username` and `postfix_send_only_relay_password` the provider's SMTP credentials. For Mailgun these are the domain's SMTP credentials, not the API key.
* `postfix_send_only_relay_sender_domain` rewrites local senders (`user@hostname`, `user@localhost`) to `user@` this domain, so the provider accepts them. Use a domain verified with the provider.

## Example Playbook

    - hosts: servers
      roles:
         - role: thermistor.postfix_send_only
           postfix_send_only_postmaster_email: you@example.com
           postfix_send_only_hostname: example.com

Relaying through Mailgun:

    - hosts: servers
      roles:
         - role: thermistor.postfix_send_only
           postfix_send_only_postmaster_email: you@example.com
           postfix_send_only_hostname: "{{ inventory_hostname }}"
           postfix_send_only_relay_host: smtp.mailgun.org
           postfix_send_only_relay_username: "{{ vault_mailgun_smtp_username }}"
           postfix_send_only_relay_password: "{{ vault_mailgun_smtp_password }}"
           postfix_send_only_relay_sender_domain: mg.example.com

To see the TLS and relay details in `/var/log/mail.log`, set `postfix_send_only_smtp_tls_loglevel: 1`.

## License

Licensed under the MIT License. See the LICENSE file for details.
