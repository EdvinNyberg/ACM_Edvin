# Examinations

Prerequisites
- A working lab environment (see [lab_environment/Vagrantfile](../lab_environment/Vagrantfile) and [lab_environment/README.md](../lab_environment/README.md))
- Ansible and the required collections (see [lab_environment/requirements.yml](../lab_environment/requirements.yml))
- A local Ansible working directory with an `ansible.cfg` and an inventory (see [02/ansible.cfg.example](02/ansible.cfg.example))

How to run
- From your Ansible working directory:
  - Use `ansible-playbook -i hosts <playbook.yml>` to run a playbook.
  - Use `ANSIBLE_LIBRARY=./library ansible -m <module> -a 'args' localhost` for custom modules (see exam 18).
- Common workflow:
  1. Ensure your VMs are up
  2. Install any required collections: `ansible-galaxy collection install -r ../lab_environment/requirements.yml`
  3. Run the playbook for the examination you want to try.

Notable files and playbooks
- Inventory / configuration example: [02/ansible.cfg.example](02/ansible.cfg.example)
- Basic playbook / package management:
  - [03/03-uninstall-software.yml](03/03-uninstall-software.yml)
- Webserver related:
  - [04/webserver.yml](04/webserver.yml)
  - [04/04-uninstall-webserver.yml](04/04-uninstall-webserver.yml)
  - [05/05-web.yml](05/05-web.yml)
  - [05/install-cert.yml](05/install-cert.yml)
  - Example https config: [05/files/https.conf](05/files/https.conf)
  - [06/06-web.yml](06/06-web.yml)
  - Web files: [06/files/example.internal.conf](06/files/example.internal.conf), [06/files/index.html](06/files/index.html)
  - Templating example: [10/10-web-template.yml](10/10-web-template.yml), [10/templates/example.internal.conf.j2](10/templates/example.internal.conf.j2)
- MariaDB / database:
  - [07/07-mariadb.yml](07/07-mariadb.yml)
  - [08/08-mariadb-config.yml](08/08-mariadb-config.yml)
  - [09/09-mariadb-password.yml](09/09-mariadb-password.yml)
- User management & file copying:
  - [11/11-users.yml](11/11-users.yml)
  - [11/11-copy-md.yml](11/11-copy-md.yml)
- Roles and refactor:
  - Roles setup helper: [12/12-create-roles](12/12-create-roles)
  - Web role tasks: [12/12-web-tasks-main.yml](12/12-web-tasks-main.yml)
  - Web handlers: [12/12-web-handler-main.yml](12/12-web-handler-main.yml)
  - DB role tasks: [12/12-db-tasks-main.yml](12/12-db-tasks-main.yml)
  - Combined roles playbook: [12/12-roles.yml](12/12-roles.yml) and example [site.yml](12/site.yml)
- Firewall:
  - [14/14-firewall.yml](14/14-firewall.yml)
- Metrics / Prometheus:
  - Controller playbook: [15/prometheus.yml](15/prometheus.yml)
  - Examination notes: [15/README.md](15/README.md)
- Advanced / project-style exercises:
  - Compliance checks: [16/README.md](16/README.md)


- Read each exam's README before running the playbook; they explain the goal and any hints.
- Use `--check` (dry-run) and `-v` / `-vv` for more output when debugging.
- Keep any vault passwords or secrets accessible (some exams expect `vault.yml` or `vars_files`).

Where to find help
- The playbooks reference Ansible built-in modules and community collections; consult the comments and each exam .
