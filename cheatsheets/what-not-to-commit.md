Never commit:
Passwords, API keys, tokens, or any other credentials — even temporarily or “just for testing.”

Personal data of other people (names, emails, photos with faces) — including classmates.

Real-world targets (IP addresses, hostnames, employee information) from systems you do not own.

Screenshots that contain credentials, session tokens, or personal information.

Any OSINT investigation data about fictional personas that could identify a real person.

Be careful with:
Lab VM IP addresses (allowed only if they are private RFC1918 addresses on your own network).

Tool outputs that include your username, hostname, or file paths revealing where you live or work.

Wireshark captures (.pcap files) — they often contain more sensitive data than expected.

Your full MAC address or full public IP — mask the last part if your repo is public.

If you accidentally commit a secret:
Treat the secret as compromised. Rotate or revoke it immediately.

Removing it in the next commit is not enough — it still exists in the Git history.

Inform the instructor and remove the secret from history using tools like git filter-repo or BFG Repo-Cleaner.
