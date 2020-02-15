Role Name
=========

install and configure ddclient to do dynamic dns update

Requirements
------------

Supported OS :
- OpenBSD (tested on 6.0)
- FreeBSD (not tested, but should be ok if binary packages can be used)
- Fedora

Role Variables
--------------
```yaml

# defaults file for ansible.ddclient
ddclient_period: 600        # seconds between run
ddclient_syslog_enable: yes # true/false to log update to syslog
ddclient_mail: root         # mail all message to this user
ddclient_mail_failure: root # mail failed update to this user
ddclient_ssl_support: yes   # if need ssl support to connect to a service

ddclient_method: 'web'      # can be either web or if or ip
ddclient_use_ip:  ''        # which static ip, required if ddclient_method is ip
ddclient_web_url: ''        # web url to get the ip, optional
ddclient_use_if:  ''        # which interface used to get the ip, required if ddclient_method is if

# this is an option in case ddclient_use_web is used
ddclient_use_web_skip: ''   # if defined, skip this string to get the ip

ddclient_protocol:          # which dydns protocol, MUST BE DEFINED !!
ddclient_login:             # user used to connect, MUST BE DEFINED !!
ddclient_password:          # password used to connect, MUST BE DEFINED !!
ddclient_server:            # server on which to connect to do ddns operation, MUST BE DEFINED !!
ddclient_hosts: ''          # which records to update, MUST BE DEFINED !!
ddclient_mx: ''             # if defined ,use it as mx for the host
ddclient_backup_mx: no      # yes or no, if ddclient_mx is a backup mx or not
ddclient_postscript: ''     # run script after updating
ddclient_wildcard: no       # yes or no, if enabled add a  * CNAME to your host

# see yml files under $ROLES/vars/ for possible OS override...
ddclient_pid: '/var/run/ddclient.pid'
ddclient_config: '/etc/ddclient.conf'
ddclient_service_name: 'ddclient'
ddclient_pkg: 'ddclient'
```

Dependencies
------------

None

Example Playbook
----------------
```yaml
- hosts:  ddclient_server
  vars:
    ddclient_method: web
    ddclient_protocol: dyndns2 
    ddclient_server: members.dyndns.org
    ddclient_login: 'mydyndns_id'
    ddclient_password: 'mydyndns_pwd'
    ddclient_ddns_records: ['myhost.dyndns-mydomain.xyz' ]
```

License
-------

BSD
