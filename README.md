# [![Unbound](lib/images/unbound-logo-small.png)](https://nlnetlabs.nl/projects/unbound) Unbound

*Install and Configure Unbound resolver*.

## Requirements

Run:
* `ansible` >=  `2.9`
* `jmespath` (Debian: `python3-jmespath`)
* `netaddr` (Debian: `python3-netaddr`)

## Supported OS

* `Debian` == `Stretch`
* `FreeBSD` == `11.2`, `12`

## Quick start

By default, unbound will listen on all interfaces, but only serve local networks. See `defaults/main.yaml`.

```yaml
roles:
  - ansible-unbound

vars:
  unbound__listen_interfaces: 
    - 127.0.0.1 # Default is 0.0.0.0
  unbound__acl:
    - "127.0.0.0/8 allow" # Default
    - "192.168.1.0/24 allow" # Default autodetect LAN
    - "0.0.0.0/0 refuse" # Default
```

## Variables

All variables have default values in `defaults/main.yaml`.

|       **Variable**          | **Mandatory** | **Type** |       **Defaults**           |
|----------------------------:|:-------------:|:--------:|:-----------------------------|
| unbound__acl                |     no        |   list   |    See `defaults/main.yml`.  |
| unbound__cron_root_hints    |     no        |  boolean |    True                      |
| unbound__do_ip6             |     no        |  boolean |    True                      |
| unbound__group              |     no        |  string  |    "unbound "                |
| unbound__listen_interfaces  |     no        |   list   |    ["0.0.0.0","::0"]         |
| unbound__listen_port        |     no        |  string  |    "53"                      |
| unbound__root_hints_url     |     no        |  string  |    See `defaults/main.yml`.  |
| unbound__service            |     no        |  string  |    "unbound"                 |
| unbound__user               |     no        |  string  |    "unbound"                 |

