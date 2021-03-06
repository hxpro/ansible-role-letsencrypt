hxpro.letsencrypt
=================

Manage LetsEncrypt challenges on a single or multi node infrastructure.
(this role is under development, do not use it at production environment)

Let's Encrypt submit all certificates to Certificate Transparency logs.
You can check your domain by: https://crt.sh/?CN=hxpro.cz

Requirements
------------

Properly set DNS for all your web nodes

Role Variables
--------------

```
le_server: 'https://acme-staging-v02.api.letsencrypt.org/directory'
le_cert_home: '/etc/pki/tls/certs/'
le_account_key: '/etc/pki/tls/private/le_account.key'
le_account_email: 'webmaster@example.com'
le_shared_key: '/etc/pki/tls/private/le_shared.key'
le_csr_home: '/etc/pki/tls/csr/'
le_payload_root: '/var/www/html/le/'
le_domains:
  - name: 'example.com'
    alt:
      - 'www.example.com'
      - 'web.example.com'
      - 'mail.example.com'
  - name: 'example.net'
    alt:
      - 'www.example.net'
le_dhparam: '/etc/pki/tls/private/dhparam.pem'
le_remaining_days: 21
```

Dependencies
------------

 - hxpro.nginx

Example Playbook
----------------

    - hosts: webservers
      roles:
        - role: hxpro.letsencrypt
          le_server: 'https://acme-v02.api.letsencrypt.org/directory'
          le_account_email: 'webmaster@example.com'

License
-------

WTFPL

Author Information
------------------

Matěj Koudelka <matej@hxpro.cz>
