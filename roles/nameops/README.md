NameOps role
============

Deploy NameOps Spring service by cloning from GitHub and building from source.

Variables
---------

- deployment_name (default: tst)
- epics_services_account (default: eicuser)
- nameops_repo_url (default: https://github.com/eicorg/NameOps.git)
- nameops_repo_version (default: main)
- nameops_java_home (derived from phoebus_dependencies_root, default target: /opt/epics-tools/lib/jvm/jdk-25)
- nameops_maven_home (derived from phoebus_dependencies_root and phoebus_dependencies_maven_version)
- nameops_http_port (default: 8080)
