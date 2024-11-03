Role Name
=========

semaphore

Requirements
--------------

Установка сервиса semaphore

Dependencies
------------
roles:
  - src: geerlingguy.nginx
  - src: geerlingguy.haproxy

collections:
  - name: community.postgresql
  - name: community.docker
