ansible-ovb
-----------

using ansible to deploy ooo on ovb setup environments

NOTE: settings are in host_vars/localhost


Running all at once to end up with an undercloud ready to do an overcloud deploy:

ansible-playbook undercloud-provision.yml undercloud-deploy.yml overcloud-deploy.yml --extra-vars "flavor=centos version=passed-ci overcloud_flavor=centos7 inventory_file_source=nodes.json"
