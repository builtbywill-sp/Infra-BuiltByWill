# 🔐 Authentication & Access

BuiltByWill systems never rely on legacy access. No passwords. No phone numbers. Just encrypted steel and sovereign keys.

---

## 🔑 Key Requirements

- **2x hardware keys required per user**
  - Must be YubiKey (5C/5Ci/Bio) or NitroKey (FIDO2/Start/3A)
  - One stays local, one is kept offsite in cold storage
  - 🔒 Mandatory for *all* system-level access, no exceptions

- **No SMS, no Google Auth, no fallback apps**
  - Yubico Authenticator or FIDO2/WebAuthn challenge only
  - Email 2FA is only allowed for passive vault observer roles

- **NFC = OFF** across all keys and systems
  - Disable NFC on YubiKey: `ykman config nfc --disable`
  - Turn off NFC at OS level on all machines

- **No passwords allowed**
  - We disable password fallback on all FIDO2 slots
  - Use this to **fully remove password fallback**:
    ```
    ykman fido access set-pin --new-pin <your-pin>
    ykman fido access set-retries --pin-retries 0 --uv-retries 0
    ykman fido access change-pin --current-pin <pin> --new-pin ""
    ```

- **Max out site config**
  - Wherever possible, set FIDO2 key challenge **character limit to 64**
  - Used for domain-bound logins or pinned identity flows
  - Example: GitHub, Proton, self-hosted vaults, and CI/CD secrets

---

## 🧱 System Access Lockdown

- ❌ No password logins (`sudo passwd -l root`)
- ❌ No password fallback on keys
- ❌ No saved secrets in `.env`, `.bash_history`, GUI password managers
- ✅ SSH and Git require FIDO2 signature
- ✅ Vault unlock requires physical key
- ✅ Git commits must be signed with registered key

---

> These aren’t just login keys. They’re reality keys.  
> If you don’t have one, you don’t exist in the system.
