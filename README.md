# Adding `verified` sign to your commits

## Install GPG Tool

[GPGTools](https://gpgtools.org/).

## Generate a new key

When installing GPG Suite it gives you the interface to generate a new one so if you prefer do it and jump to the next topic.

### Generating through terminal

Generates a new key:

```bash
gpg --gen-key
```

You'll need to inform:
- Name
- Email
- Password

### Listing the keys

List the keys and copy the one you've just generated.

```bash
gpg --list-secret-keys --keyid-format LONG
```

In the first line at `sec` copy the last key which is the longest one.

```bash
gpg --armor --export <key>
```

## Adding at Github account 

Paste the previously generated key at [Github GPG new key](https://github.com/settings/gpg/new).

## Associating Git with the GPG key

The same way as the longest key copy the shortest key after `rsa2048/` in the same line of `sec`.

```bash
gpg --list-secret-keys --keyid-format LONG
```

Copy the key and add individually the config below:

```bash
git config --local user.signingkey <key>
git config --local gpg.program gpg2
git config --local commit.gpgsign true
```
## References

- [Generating a new GPG key](https://help.github.com/en/github/authenticating-to-github/generating-a-new-gpg-key)
- [Adding a new GPG key to your GitHub account](https://help.github.com/en/github/authenticating-to-github/adding-a-new-gpg-key-to-your-github-account)
- [Signing commits with GPG](https://docs.gitlab.com/ee/user/project/repository/gpg_signed_commits/)
