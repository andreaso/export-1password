## Export and Encrypt 1Password Vaults

This _ee1pw_ script uses the [1Password CLI][1] to produce an
[GnuPG][2] encrypted export of your 1Password Vault records.

### Usage

Before using the backup script for the first time you will need to
perform a "full" signin, having the CLI setup your _~/.config/op/config_ file.

```
op signin my.1password.com foo.bar@example.com
```

After that you just call the script directly, and it will prompt you
for your Master Password.

```
./ee1pw --gpg-key 0x1234567890ABCDEF
```

Assuming everything goes well an encrypted tarball will be created in
your current working directory.


### Potential Questions

#### Why the double layer of encryption?

1. The individual json files are encrypted to make it easier to
   recover individual records, without unnecessarily exposing all
   other records.

2. The collective tarball is encrypted to protect the Vault titles and
   the record titles, which may or may not be of a private nature.


[1]: https://1password.com/downloads/command-line/
[2]: https://gnupg.org/
