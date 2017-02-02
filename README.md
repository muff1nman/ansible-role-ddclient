Role Name
=========

install and configure ddclient to do dynamic dns update

Requirements
------------

OS currently supported by role:
- OpenBSD

Role Variables
--------------
* ddclient_method: 'web'  
can be either 'web' or 'if' or 'ip'

* ddclient_use_ip: ''         
with the correct static ip, REQUIRED when ddclient_method: 'ip'

* ddclient_web_url: ''	    
web url to get the ip, if ddclient_method: 'web'

* ddclient_use_if: ''         
which interface used to get the ip, REQUIRED when ddclient_method: 'if'

*Others options that also MUST BE DEFINED :*
* ddclient_protocol: ''      
which dydns protocol

* ddclient_login: ''         
user used to connect

* ddclient_password: ''       
password used to connect

* ddclient_server: ''         
server on which to connect to do ddns operation

* ddclient_ddns_records: []   
which records to update

*Theses are default options that can be overriden :*
* ddclient_period: 600
seconds between run

* ddclient_syslog_enable: yes
true/false to log update to syslog

* ddclient_mail: root            
mail all message to this user

* ddclient_mail_failure: root    
mail failed update to this user

* ddclient_ssl_support: yes      
if need ssl support to connect to a service

* ddclient_use_web_skip: ''   
this is an option in case ddclient_use_web is used, if defined, skip this string to get the ip

* ddclient_mx: ''             
if defined ,use it as mx for the host, this has to be supported by the dyn hoster...

* ddclient_backup_mx: no      
yes or no, if ddclient_mx is a backup mx or not, this has to be supported by the dyn hoster...

* ddclient_postscript: ''     
run script after updating

* ddclient_wilcard: no        
yes or no, if enabled add a  * CNAME to your host, this has to be supported by the dyn hoster...

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
