# CCDC Strategy and Documentation

## A note on the enclosed information
This information is **HIGHLY-CONFIDENTIAL**. Period. Do not share it with *ANYONE* outside of the club. No Normies allowed (Ree).

## Nationals 2019 Linux

### Starting Off

4 admins:
* 1 Secure local ESXi
* 1 Secure cloud ESXi
* 1 Spray SSH change creds script (root & admin users)
  * Manually change passwords on failed boxes
* 1 Login to web apps and change admin passwords

### Strategy

* Jumphost - super secure
* SSH remote mount everything - use for:
  * Backups
  * Changing web app passwords
  * Malware scans

### Useful commands
* RHEL verify all packages: `rpm -Va`
  * Output only if different, checks perms and hashes
* Debian verify all packages: `debsums`
  * Need to install

### Needed scripts
* Panolpy-style set root ssh PubKey and kick everyone else out script
* Ansible Tasks:
  * Backup
    * Backup /home and /srv on all systems
  * Firewall
    * Set firewall to log and connection limit
  * Setup
    * Install tripwire & setup
    * Install fail2ban on ssh servers
    * Install mod_evasive and mod_security (?) on web servers
  * Status
    * Run `w` and `netstat -planet` and `ss`, filter and print for all servers
    * Cat access logs and filter for all web servers
    * Cat auth logs and filter for all ssh servers
    * Tripwire status
  * Users
    * Add linuxuser
    * Add list of users from CSV
    * Change all user passwords
    * Change all root passwords
  * Other ??
