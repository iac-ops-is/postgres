Postgres
=========

Роль ставит простецкий pg кластер из мастера и реплик. Не поднимает балансер.


Role Variables
--------------

| | | |
|-|-|-|
|переменная| описание | дефолтное значение |
|postgres_data_directory | путь до папки с данными | var/lib/postgresql/data
|postgres_replica_password| пароль для роли репликации |supersecretpassword|
|postgres_need_replication| нужно ли создавать кластер с репликами|false|
|postgres_master_host| хост мастера postgres |первый хост в группе db|
|postgres_sync_replica_hosts| список хостов, которые станут синхронными репликами|[]|
|postgres_async_replica_hosts|список хостов, которые станут асинхронными репликами |[]|
|postgres_user| имя пользователя |postgres|
|postgres_user_password| пароль пользователя|postgres|
|postgres_db| название базы данных |postgres|

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - name: deploy postgres cluster
		become: yes
		hosts: db
		roles:
			- postgres
		vars:
			postgres_data_directory: /data
			postgres_replica_password: ushed9duiad23j390e1=
			postgres_need_replication: true
			postgres_sync_replica_hosts:
				- 192.168.56.202
			postgres_async_replica_hosts:
				- 192.168.56.203
			postgres_user: user
			postgres_user_password: user
			postgres_db: db

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
