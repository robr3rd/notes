# General PGP (Pretty Good Privacy) info
## Encrypt
> You can only encrypt **files**; you cannot encrypt **folders**. If you need to encrypt a group of files, then they should be packed into an archive (e.g. `tar -czf [output-archive].tar.gz [input]`)

### Symmetric
Symmetric authentication is used when you only want to password-protect something. Note that this is *NOT* full "PGP" encryption as is preferred (wherein Keypairs for both parties are exchanged), although it is incredibly useful in instances where the receiving party does not have a PGP keypair of their own or if you *want* the encrypted data to opened by more than a limited set of recipients.

```sh
gpg --symmetric --sign --force-mdc --cipher-algo AES256 --output [encrypted-output].gpg [input]
```

- `--symmetric` - Explained above
- `--sign` - Sgns it with your Private Key so that the recipient can verify/trust the origin
- `--force-mdc` - Force integrity checks...basically this just suppresses a "WARNING" message that would otherwise appear when the recipient tries to decrypt the file
- `--cipher-algo AES256` - Force better encryption algorithm to be used
- `--output [encrypted-output].gpg` - What to name the result of the encryption process
- `[input]` - The file (e.g. `.txt`, `.sh`, `.cert`, `.ca`, `.key`, etc.) or folder/archive (`.tar.gz`, `.bz2`, `.7z`, etc.)
	- Note that only files and archives (which are still technically file resources) can be provided as input...standard directories cannot be.

## Decrypt

### Symmetric
```sh
gpg --output [output] [input-encrypted].gpg
```

- `--output [output]` - The result of the decryption process (e.g. `secure.txt`, `ssl-cert.tar.gz`, etc.)

> Helpful hint: If the output is a `.tar.gz` archive, then this command can be used to unpack it: `tar -xvzf [archive].tar.gz`
