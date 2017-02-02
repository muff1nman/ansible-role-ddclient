Role Name
=========

install and configure ddclient to do dynamic dns update

Requirements
------------

OS currently supported by role:
- OpenBSD

Role Variables
--------------

you  MUST DEFINED onr of theses 3 :

* ddclient_use_ip: ''         
with static ip

* ddclient_use_web: ''	    
web url to get the ip

* ddclient_use_if: ''         
which interface used to get the ip


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

* ddclient_protocol: ''      
which dydns protocol, MUST BE DEFINED !!

* ddclient_login: ''         
user used to connect, MUST BE DEFINED !!

* ddclient_password: ''       
password used to connect, MUST BE DEFINED !!

* ddclient_server: ''         
server on which to connect to do ddns operation, MUST BE DEFINED !!

* ddclient_ddns_records: ''   
which records to update, MUST BE DEFINED !!

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

TODO 

License
-------

BSD
