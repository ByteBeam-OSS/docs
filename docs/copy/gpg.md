# Generating a Key with GPG

This guide provides step-by-step instructions on generating both Ed25519 and RSA keys using GPG.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Generating an Ed25519 Key](#generating-an-ed25519-key)
- [Generating an RSA Key](#generating-an-rsa-key)
- [Managing GPG Keys](#managing-gpg-keys)

## Prerequisites

- GnuPG installed.

## Generating an Ed25519 Key

1. **Open a Terminal or Command Prompt**.

2. **Initiate Key Generation**:
   ```bash
   gpg --expert --full-generate-key
   ```

3. **Select Key Type**:
   - Choose `(E) ECC and ECC` when prompted.

4. **Choose the Curve**:
   - Select `Ed25519`.

5. **Set Key Expiry**:
   - Recommended: `2y` (or less) for a balance between security and convenience.

6. **Enter User Details**:
   - Real name: Your name.
   - Email address: Your email.
   - Comment: Optional.

7. **Set a Strong Passphrase** to protect your private key.

8. **Verify Key Generation**:
   ```bash
   gpg --list-keys your_email@example.com
   ```

## Generating an RSA Key

1. **Open a Terminal or Command Prompt**.

2. **Initiate Key Generation**:
   ```bash
   gpg --full-generate-key
   ```

3. **Select Key Type**:
   - Choose `(1) RSA and RSA`.

4. **Key Size**:
   - Choose `4096` bits for enhanced security.

5. **Set Key Expiry**:
   - Recommended: `2y` (or less) for a balance between security and convenience.

6. **Enter User Details**:
   - Real name: Your name.
   - Email address: Your email.
   - Comment: Optional.

7. **Set a Strong Passphrase** to protect your private key.

8. **Verify Key Generation**:
   ```bash
   gpg --list-keys your_email@example.com
   ```

## Managing GPG Keys

### Deleting a Key

1. **List All Keys**:
   ```bash
   gpg --list-keys
   ```

2. **Delete the Desired Key**:
   ```bash
   gpg --delete-keys KEY_ID
   ```

3. **Confirm Deletion** when prompted.

4. **Delete the Associated Private Key (if needed)**:
   ```bash
   gpg --delete-secret-keys KEY_ID
   ```

---

# Configuring Thunderbird with GPG

This guide provides step-by-step instructions on integrating Thunderbird with GPG for secure email communication.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Configuring Thunderbird](#configuring-thunderbird)

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

