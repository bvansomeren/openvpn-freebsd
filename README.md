bvansomeren.openvpn-freebsd-server
=========

Installs OpenVPN from pkg, creates the CA and creates client certificates.  
Some TODO issues:  
* Removal of users
* Extending certificates
* Use EasyRSA to manage certificates, CA etc.


Requirements
------------

Tested with FreeBSD 11 base; Does not work in a Jail.
TODO: Setup jail using VMIMAGE

Role Variables
--------------

Too many to list; Have a look at defaults/main.yml
See also the minimal example listed below.

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: freebsd-test1
  	   user: nonpriv\_user
  	   become: yes
  	   become\_user: root
  	   vars:
    	 openvpn_default_server_ip: "10.2.1.0 255.255.255.0"
    	 openvpn_port: 443
    	 openvpn_proto: tcp
    	 openvpn_configuration:
    	 - name: comp-lzo
    	 openvpn_client_configuration:
    	 - name: comp-lzo
    	 openvpn_clients:
    	 - cn: user1
      		validity: 3650
    	 - cn: user2-password
      	 	validity: 365
      		password: somesecurepassword
    	 openvpn_client_push_routes:
    	 - "10.2.0.0 255.255.255.0"
  	 	 roles:
  		 - bvansomeren.openvpn-freebsd-server

License
-------

BSD

Author Information
------------------

