Rol Jboss Datagrid 8
=========

[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-jboss_datagrid8-blue.svg)](https://galaxy.ansible.com/CyVerse-Ansible/jbos-datagrid8/)

Instalacion de JBoss Datagrid 8 en RHEL.

Requisitos
------------

- Subscripcion de RHEL.
- Inventario compuesto por subgrupos referenciando cada uno de los Clusters.



Ejemplo del inventario

        datagrid:
            children:
                cluster_1:
                    hosts:
                        vm_1:
                            ansible_host: 192.168.0.30
                cluster_2:
                    hosts:
                        vm_2:
                            ansible_host: 192.168.1.32


Variables del rol
--------------

| Name | Default | Description
| ------ | ------ | ------ |
| datagrid_zipfile | "../redhat-datagrid-8.0.0-server.zip"  | Ruta del archivo zip de instalacion |
| datagrid_install_path | "/APLICACIONES/DATAGRID/" |  Ruta de instalacion de Datagrid |
| datagrid_path | "/APLICACIONES/DATAGRID/redhat-dathagrid-8.0.0-server" | Ruta completa al server path de Datagrid |
| packages_to_install | "[gzip, java-1.8.0-openjdk-devel]" |Lista con los paquetes necesarios a instalar |
| service_user_uid | "9403" | uid del usuario de servicio en systemd |
| cache_name  | "sso"  | Nombre de la cache a generar |

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
            service_user_uid:
            cache_name: sso