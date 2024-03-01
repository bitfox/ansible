Role Name
=========

Die Rolle cmk_agent kann dem CMK-Agenten auf einer Linux-Maschine ausrollen und am CMK-Server
- in einem Hostfolder anlegen
- ein vollständiges Discovery durchführen
- die Service-Items übernehmen
- die TLS-Verschlüsselung aktivieren

Requirements
------------

Auf den Zielmaschinen wird das Paket "curl" vorausgesetzt.

Es wird ein Linux auf Basis CentOS, Rhel, Debian in Version 7-9 erwartet.

Die letzten verfügbaren rpm- und deb-Pakete müssen zu Beginn in das Verzeichnis "cmk_agent/files" gespeichert,
als auch die Variablen der Rolle wie folgt angepasst werden.

Role Variables
--------------

Unter defaults/main.yml sind die Basis-Variablen für CMK definiert:

- Die URL des CMK-Servers
  cmk_server_name: "checkmk.mynetwork.local"
- Die IP des CMK-Servers
  cmk_server_ip: "10.0.0.10"
- Der Name der CMK-Site ( https://server/SITE/... )
  cmk_site: "monitoring"
- Der Name des Ordners, in dem der jeweilige Host abgelegt werden soll
  cmk_folder: "/"
- Die Daten des Funktionsbenutzers
  cmk_automation_user_name: "***youdontknowyack***"
  cmk_automation_user_password: "***youdontknowyack***"
- Die Firewall-Zone für firewalld
  cmk_cliuent_zone: "public"
- Die alternativen Installationspakete des cmk-agenten, wenn dieser nicht im Repository gefunden werden kann:
  ( Diese Dateien werden aus files/ an das Ziel kopiert und installiert. )
  cmk_package_rpm: "check-mk-agent-2.2.0p17-1.noarch.rpm"
  cmk_package_deb: "check-mk-agent_2.2.0p17-49385346971f6457_all.deb"


Dependencies
------------

Für das Bearbeiten von Firewalld wird das entsprechende Paket benötigt:

 ansible-galaxy collection install ansible.posix
bzw. kann das Paket

  https://galaxy.ansible.com/ui/dispatch/?pathname=%2Fansible%2Fposix

hier herunter und manuell installiert werden.



Example Playbook
----------------

Ein Playbook kann wie folgt aufgesetzt werden:


    - hosts: all
      roles:
        - role: cmk_agent


License
-------

BSD

Author Information
------------------

2024-01-06 Oliver Lenz
