# vpn_setup_on_alicloud
How to setup VPN on your alicloud server

## Install

```shell
git clone git@github.com:kelvinji2009/vpn_setup_on_alicloud.git
cd vpn_setup_on_alicloud
chmod a+x vpn_setup_on_alicloud.sh
```



## Quick Start 

### Peer setup

* Create new peer, for example `hk1`

```shell
sudo touch /etc/ppp/peers/hk1 # hk1 is the peer name
sudo vim /etc/ppp/peers/hk1
```

Paste the configurations as below and feel free to change it as your requirement:

```
remotename hk1
linkname hk1
ipparam hk1
pty "pptp [YourServerDomainOrIP] --nolaunchpppd "
name [YourAccount]
usepeerdns
require-mppe
refuse-eap
noauth
```

* Setup authentication

```
sudo vim /etc/ppp/chap-secrets
```

Paste the configurations as below and feel free to change it as your requirement:

```
# Secrets for authentication using CHAP
# client	server	secret			IP addresses
[YourAccount] hk1    [YourPassword]          *
[YourAccount] hk2    [YourPassword]          *
[YourAccount] hk3    [YourPassword]          *
```

### Run

```
cd vpn_setup_on_alicloud
./vpn_setup_on_alicloud.sh hk1 start
```

Enjoy it now. :D

## Usage 

```
./vpn_setup_on_alicloud.sh VPN_CONFIG_NAME ACTION[start|stop]
```

