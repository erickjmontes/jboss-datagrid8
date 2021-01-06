Rol Jboss Datagrid 
=========

Instalacion de JBoss Datagrid 8 en RHEL.

Requisitos
------------

Red Hat Subscription.

Variables del rol
--------------

Name 	Default Value 	Description
`` 	``
datagrid_zipfile  "../redhat-datagrid-8.0.0-server.zip"   Ruta del archivo zip de instalacion
datagrid_install_path "/APLICACIONES/DATAGRID/"   Ruta de instalacion de Datagrid
datagrid_path "/APLICACIONES/DATAGRID/redhat-datagrid-8.0.0-server" Ruta completa al server path de Datagrid
packages_to_install "[gzip, java-1.8.0-openjdk-devel]"    Lista con los paquetes necesarios a instalar
service_user_uid  "9403"  uid del usuario de servicio en systemd para Datagrid

Dependencias
------------

Paquetes:
* unzip
* java-1.8.0-openjdk

Nuestro playbook provee esas dependencias en tasks/setup.yml

Playbook de ejemplo
-------------------

    - hosts: datagrid

      roles: 
        - jboss_datagrid
      vars:
        datagrid_zipfile: ../redhat-datagrid-8.0.0-server.zip
        datagrid_install_path: /APLICACIONES/DATAGRID/
        datagrid_path: /APLICACIONES/DATAGRID/redhat-datagrid-8.0.0-server
        packages_to_install:
            - java-1.8.0-openjdk-devel
            - unzip
