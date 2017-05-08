# Postgres Backups
## Backup Setup
1. Create new hostfile containg two variables:
`[backup-server]`
`backup-server`
`[backup-client]`
`server-to-be-backed-up`


2. Run playbook:
`ansible-playbook setup-backup.yml -i {{ inventory }} -e "user={{ your_user }} backed_server={{ desired backup name}}" -kK`

-k if not ssh key loaded

