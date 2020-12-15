# Hardening

For this task, I think I'll just cover bare minimum:

* Check sshd config for protocol ver, logging, etc
* Disable root ssh access (if switching to `without-password` - use `ssh -i ~/.ssh/id_rsa_oxy root@IP_REDACTED` to log in)
  * Create user and add it to wheel or whatever admin group in Debian is (user `ackrite`)
  * Ideally you'd probably also add password length checks and other stuff but that would most likely be handled my AD in any corp environment.
* `/tmp` stuff
  * Move to separate tmpfs by adding entry to fstab
  * Add `nodev, nosuid, and noexec`
* Add either `fail2ban` or `crowdsec` or equiv since this is an internet facing server.

In general, if tasked with this I'd go over RHEL Hardening guide, also dependent on user requirements.
