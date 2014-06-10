LittleCrypt
===========

Think of it as chef-vault for littlechef.


Standalone Usage
----------------

Encrypt `mail_pem` secret in `secrets` data bag using kitchen's and node public keys:

```
littlecrypt create -b secrets -n mail_pem --nodes dummy,foobar --secret "secret data"
```

Or you can just point to secret from file:

```
littlecrypt create -b secrets -n mail_pem --nodes dummy,foobar --secret-file mail.pem
```

Show decrypted secret using kitchen's private key:

```
littlecrypt show -b secrets -n mail_pem
```


Usage in recipes
----------------

Decrypt `mail_pem` secret from `secrets` data bag using node's private key:

```ruby
include_recipe "littlecrypt"

LittleCrypt::Item.load("secrets", "mail_pem")
```
