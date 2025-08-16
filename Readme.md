# Postgres role

This role will install Postgresql database (if it not presented), and create a user with credentials.


## Also this role uses custom module `module/postgres`, which can be useful

Module is declarative-style and use a `psql` cli tool & os.system syntax to prefer operations with database. 
The playbook for this module can look like this:
```yaml

- name: Transfer db template
  ansible.builtin.file:
    src: path/to/template.psql.j2
    dest path/on/host/temp.psql


- name: Database for sales
  postgres:
    user:
      name: jonh
      password: 12345 # optional
      auth:
        type: host  # default is peer 
        method: md5 # use md5 validation 
        args: 192.168.1.0/24 # network to allow 
      db_names:
            - jonhdb
      db_schemas:
            - path/oh/host/temp.psql
      become: true
```

This playbook will copy database template in sql syntax and, if this state not present on host, create roles, permissions, etc.

### Supported args
--- 








