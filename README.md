### A List of Common Commands, Procedures, and Information
---

A personal reference sheet (easy copy/paste) and script repository for everything from typical fresh-install commands to complete configurations. Mostly setup for my own use, but feel free to add a pull request if there's anything that should be added or changed.

---

## CentOS

Update, upgrade, clean:
```sh
yum update -y && yum upgrade -y && yum autoremove -y && yum clean all
```

Install Epel, update, upgrade, clean:
```sh
yum install -y epel-release && yum update -y && yum upgrade -y && yum autoremove -y && yum clean all
```

Basic tools install: `yum install -y wget nano htop bzip2 zip unzip screen `

Extra tools install: `yum install -y atop nload smartmontools java`

Upgrade from minimal install: `yum groupinstall "Base"`

List jails (Fail2Ban): `fail2ban-client status`

List banned IPs in single jail (Fail2Ban): `fail2ban-client status JAIL`

List all banned IPs (Fail2Ban):
```sh
fail2ban-client status | grep "Jail list:" | sed "s/ //g" | awk '{split($2,a,",");for(i in a) system("fail2ban-client status " a[i])}' | grep "Status\|IP list"
```

Unban IP (Fail2Ban): `fail2ban-client set JAIL unbanip IP`

---

## Ubuntu

Update, upgrade, clean:
```sh
apt-get update -y && apt-get upgrade -y && apt-get --purge autoremove -y && apt-get clean
```

Basic tools install: `apt-get install -y wget nano htop bzip2 zip unzip screen`

Extra tools install: `apt-get install -y atop nload smartmontools java`

List jails (Fail2Ban): `fail2ban-client status`

List banned IPs in single jail (Fail2Ban): `fail2ban-client status JAIL`

List all banned IPs (Fail2Ban):
```sh
fail2ban-client status | grep "Jail list:" | sed "s/ //g" | awk '{split($2,a,",");for(i in a) system("fail2ban-client status " a[i])}' | grep "Status\|IP list"
```
