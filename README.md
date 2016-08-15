ssl_certificates
================

Install and manage SSL certificates and private keys. The certificates
and keys may be specified as variables or as files.

Make sure that the private key content/file is stored in an encrypted
form when commited to the repository. git-crypt provides this
capability.

Example Playbook
----------------

    # Using Variables
    - hosts: servers
      vars:
        ssl_certificates:
         - name: certname.crt
           content: |
             -----BEGIN CERTIFICATE-----
             ....
             -----END CERTIFICATE-----
        ssl_private_keys:
         - name: certname.key
           content: |
             -----BEGIN RSA PRIVATE KEY-----
             ....
             -----END RSA PRIVATE KEY-----
      roles:
         - ssl_certificates

    # Using files
    - hosts: servers
      vars:
        ssl_certificate_files: [ certname.crt ]
        ssl_private_key_files: [ certname.key ]
      roles:
         - ssl_certificates

Role Variables
--------------

 * ssl_certificates: []

    Specifies a list of SSL certificates to install on the server. Each
    item should include 'name' and 'content' keys.

 * ssl_private_keys: []

    Specifies a list of SSL private keys to install on the server. Each
    item should include 'name' and 'content' keys.

 * ssl_certificate_files: []

    Specifies a list of SSL certificate files to copy to the server.
    The destination file will have the same name as the local file.

 * ssl_private_key_files: []

    Specifies a list of SSL private key files to copy to the server.
    The destination file will have the same name as the local file.

Role Handlers
-------------

none.
