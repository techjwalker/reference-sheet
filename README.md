<p align="center">
    <a href="https://github.com/techjwalker/reference-sheet/issues">
        <img src="https://img.shields.io/github/issues-raw/techjwalker/reference-sheet.svg?style=flat-square"
             alt="Issues">
    </a>
    <a href="https://github.com/techjwalker/reference-sheet/pulls">
        <img src="https://img.shields.io/github/issues-pr-raw/techjwalker/reference-sheet.svg?style=flat-square"
             alt="Pull Requests">
    </a>
    <a href="https://github.com/techjwalker/reference-sheet/graphs/contributors">
        <img src="https://img.shields.io/github/contributors/techjwalker/reference-sheet.svg?style=flat-square"
             alt="Contributors">
    </a>
    <a href="https://github.com/techjwalker/reference-sheet">
        <img src="https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat-square"
             alt="Contribs Welcome">
    </a>
</p>
<p align="center">
    <a href="https://tastynode.com">
        <img src="https://img.shields.io/badge/sponsored%20by-tastynode.com-red.svg?style=flat-square"
             alt="TastyNode.com">
    </a>
</p>

Reference Sheet
=======

A List of Common Commands, Procedures, and Information.

A personal reference sheet (easy copy/paste) and script repository for everything from typical fresh-install commands to complete configurations. Mostly setup for my own use, but feel free to add a pull request if there's anything that should be added or changed.

Common Commands
---------------

This set of common commands are used more frequently, especially when working with a newly installed system. For specific use-case commands, check the corresponding section. If a command is missing here, and seems like it would be beneficial to add, create a pull request to add the changes.

### CentOS

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

### Ubuntu

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
