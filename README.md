# Ansible Playbook for Postgres Backups using 2nd Quadrant Barman Backup tool
## General

Ansible playbook used for setting up 2nd Quadrant Barman PostgreSQL backup for PostgreSQL server http://www.pgbarman.org/.
This backup is setup in the mode for the: backup over rsync + streaming replica. 
In order to use:
- Streaming replica
- Data deduplication and compression

Requirements:
- Network connections:
-- from backup server to backed server TCP 22/5432 port open
-- from backed server to backup server TCP 22
- Connection entry on PGHBA.conf allow connect from backup server to backed server
- Sudo permissions for user what creates backup either proper setup of sudo delegation

## Backup Setup
1. Create new hostfile containg two variables:
`[backup-server]`
`backup-server`
`[backup-client]`
`server-to-be-backed-up`


2. Run playbook:
`ansible-playbook setup-backup.yml -i {{ inventory }} -e "user={{ your_user }} backed_server={{ desired backup name}}" -kK`

-k if not ssh key loaded

