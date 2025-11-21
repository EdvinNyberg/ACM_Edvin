# Examination 7 - MariaDB installation

To make a dynamic web site, many use an SQL server to store the data for the web site.

[MariaDB](https://mariadb.org/) is an open-source relational SQL database that is good
to use for our purposes.

We can use a similar strategy as with the _nginx_ web server to install this
software onto the correct host(s). Create the playbook `07-mariadb.yml` with this content:

    ---
    - hosts: db
      become: true
      tasks:
        - name: Ensure MariaDB-server is installed.
          ansible.builtin.package:
            name: mariadb-server
            state: present

# QUESTION A

Make similar changes to this playbook that we did for the _nginx_ server, so that
the `mariadb` service starts automatically at boot, and is started when the playbook
is run.

# QUESTION B

When you have run the playbook above successfully, how can you verify that the `mariadb`
service is started and is running?

A: I ran 'ansible db -a "systemctl status mariadb"'. You can also ssh into the dbserv and run 'systemctl status mariadb'.

# BONUS QUESTION

How many different ways can use come up with to verify that the `mariadb` service is running?

A:
1. systemctl status mariadb, shows service state.
2. systemctl is-active mariadb, returns "active" if running.
3. systemctl is-enabled mariadb, shows if it starts at boot.
6. mysql -u root -e "SELECT VERSION();", if this returns a version, the server is working.
7. ansible db -m service_facts, ansible service inventory.
8. ansible db -a "systemctl status mariadb", remote command via Ansible.
