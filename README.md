ansible-ovb
-----------

using ansible to deploy ooo on ovb setup environments. These playbooks assume
1) baremetal nodes already exist and are configured for your tenant.
2) you have a nodes.json already constructed (see #1).
3) you have a floating ip

Put your cloud credentials in host_vars/localhost.


playbooks:
undercloud-provision.yml - sets up the undercloud node and gets it current (yum update/reboot)
undercloud-deploy.yml - goes throughthe undercloud setup process to end up with a functioning undercloud
overcloud-deploy.yml - loads OVB inventory, introspection and overcloud image build (DOES NOT DEPLOY OVERCLOUD)


Running all at once to end up with an undercloud ready to do an 'openstack overcloud deploy':

ansible-playbook undercloud-provision.yml undercloud-deploy.yml overcloud-deploy.yml --extra-vars "flavor=centos version=passed-ci overcloud_flavor=centos7 inventory_file_source=nodes.json"
