# Ansible Create Subscription

Has 2 modes, where either the script is run after a memberpress subscription is created, this causes a digitalocean droplet to be created. Or a 'byo account' is created and the user connects their own server at provision stage.

# MemberPress Mode

INPUT (extra_variables):
client_first_name
client_last_name
client_email
member_id - login username, a memberpress member number (eg: '25')
subscription_id - memberpress subscription number (eg: 'mp-sub-5fa2a2ac5fa12')
plan_title - size of server is using memberpress ('Micro Server', 'Small Server', 'Medium Server', 'Large Server', 'Jumbo Server'), if making a BYO server this can be left blank and defined later at provision stage.

PROCESSING: Creates AWX Account for user, creates initial organisation.yml and server_vars.yml file. Creates a DigitalOcean droplet and space. Also creates initial '{{ subscription_id }} Provision Server' playbook in users account.

OUTPUT: Working AWX account at provision stage.

# BYO Mode

INPUT (extra_variables):
client_first_name
client_last_name
client_email
member_id - login username, a string (eg: 'billybob')
subscription_id - 'byo'

PROCESSING: Creates AWX Account for user, append random string to 'byo', creates initial organisation.yml and server_vars.yml file. Also creates initial '{{ subscription_id }} Provision Server' playbook in users account.

OUTPUT: Working AWX account at provision stage.
