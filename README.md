Role Name
=========

Install rsync as deamon and create shares

Requirements
------------

This role support at this moment only debian/ubuntu systems

Role Variables
--------------

rsync:
  config_dir: "/etc/rsync"
  config_file: "/etc/rsync/rsyncd.conf"
  directores:
    - path: "/mnt/productive/data"
      owner: root
      group: root
      mode: 0644
  default:
    max_connections: 1
    log_file: "/var/log/rsyncd.log"
    timeout: 300
  shares:
    - name: "productive"
      set:
       comment: "productive"
       path: "/mnt/productive/data"
       list: "yes"
       uid: "root"
       read_only: "false"
       hosts allow: "127.0.0.1"

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: yamb00.rsync}

License
-------

BSD

Author Information
------------------
