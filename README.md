# Ansible role Self-Signed Certificates

[![CI](https://github.com/supertarto/ansible-role-self-cert/workflows/ci.yml/badge.svg)](https://github.com/supertarto/ansible-role-self-cert/actions/workflows/ci.yml)

Create self-signed certificates with Ansible, with our without your own CA. Used for test environment.

## Requirements

None

## Tested plateform

* Debian 12 (Bookworm)
* Debian 13 (Trixie)

## Role variables

True if you want to create a self-cert signed certificate with your own CA. The CA will be created by this role.
```yml
cert_use_ownca: true
```

Your private key path and your csr path.
```yml
cert_private_key_path: "/etc/ssl/private/"
cert_csr_path: "/etc/ssl/csr"
```

Owner and group of your certificates.
```yml
cert_owner: "root"
cert_group: "ssl-cert"
```

Type and size of your CA key. Only used if **cert_use_ownca** is True.
```yml
cert_ca_type: "RSA"
cert_ca_size: "4096"
```

Information about your CA. Only used if **cert_use_ownca** is True. For the SAN, if needed, **You have to add "IP:" or "DNS:" before your alternate name**
```yml
cert_ca_country_name: "FR"
cert_ca_organization_name: "My Orga Name"
cert_ca_mail_address: "admin_mail@example.com"
cert_ca_common_name: "my_ca_name"
cert_ca_san: []
  # Example - YOU MUST ADD THE PREFIX - DNS OR IP
  # - "DNS:alternative_name.example.com"
  # - "IP:192.168.1.1"

cert_ca_basic_constraint: []
  # Exemple:
  # - CA:TRUE
```

Path where the CA cert will be created.
```yml
cert_ca_path: "/etc/ssl/cert"
cert_ca_provider: self-signed
```

Information about the cert. Path, type of key, size.... For the SAN, if needed, **You have to add "IP:" or "DNS:" before your alternate name**
```yml
cert_path: "/etc/ssl/cert"
cert_common_name: "my_cert_common_name"
cert_type: "RSA"
cert_size: "4096"
cert_country_name: "FR"
cert_organization_name: "My Orga Name"
cert_mail_address: "admin_mail@example.com"
cert_provider: self-signed
cert_san: []
  # Example - YOU MUST ADD THE PREFIX - DNS OR IP
  # - "DNS:alternative_name.example.com"
  # - "IP:192.168.1.1"
cert_basic_constraint: []
  # Exemple:
  # - CA:FALSE
```

## License

GPL V3.0
