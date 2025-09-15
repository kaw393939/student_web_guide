### Module 05 — SSH Keys & GitHub Access (30–45 minutes)

Goal: generate an SSH keypair, add the public key to GitHub, and verify access.

Estimated time: 30–45 minutes

Tasks

1) Check for existing SSH keys

```bash
ls -la ~/.ssh
```

2) Generate a new key (if needed)

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
# accept defaults, enter a passphrase or leave empty (teacher's choice)
```

3) Add public key to GitHub

```bash
cat ~/.ssh/id_ed25519.pub
```

- Copy the output and paste into GitHub → Settings → SSH and GPG keys → New SSH key.

4) Test connection

```bash
ssh -T git@github.com
```

Expected output: a welcome message that confirms authentication.

Deliverable: screenshot or pasted success message from `ssh -T git@github.com`.

Teacher notes
- If students can't add keys due to GitHub account restrictions, use a teacher-provided org repo or fallback to HTTPS with token.

---
