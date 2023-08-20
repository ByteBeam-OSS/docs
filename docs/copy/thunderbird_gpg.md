# Configuring Thunderbird with GPG

This guide provides step-by-step instructions on integrating Thunderbird with GPG for secure email communication.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Configuring Thunderbird](#configuring-thunderbird)
- [Additional Information](#additional-information)
- [References](#references)

## Prerequisites

- Thunderbird installed.
- GnuPG installed.

## Configuring Thunderbird

1. **Open Thunderbird**.

2. **Access Configuration Editor**:
   - Navigate to: Thunderbird → Settings → General → Config Editor.

3. **Enable External GnuPG**:
   - Search for `mail.openpgp.allow_external_gnupg`.
   - Set its value to `true`.

4. **Restart Thunderbird** for the changes to take effect.

## Additional Information

- **Direct Integration Limitation**: Thunderbird does not directly utilize the existing GPG keyring for public keys. This is a design choice by Thunderbird. Users might have to maintain two databases with the same content, storing contacts' trusted keys and their level of trust.

- **Using GPG-Agent with Thunderbird**: While direct integration is not possible, Thunderbird can be configured to use GnuPGP's `gpg-agent`. This allows Thunderbird to use the keys of GnuPGP. For more details, refer to the [Mozilla wiki page](https://wiki.mozilla.org/Thunderbird:OpenPGP:Smartcards#Allow_the_use_of_external_GnuPG). Note that the page primarily discusses smartcards, but the linked section is generic about using `gpg-agent` with Thunderbird.

## References

- [SuperUser Discussion on Thunderbird and GPG Keyring](https://superuser.com/questions/1758464/how-do-i-get-thunderbird-to-use-my-gpg-keyring)

