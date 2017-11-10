ansible-ovb
-----------

using ansible to deploy ooo on ovb setup environments. These playbooks assume
1. baremetal nodes already exist and are configured for your tenant.
2. you have a nodes.json already constructed (see #1).
3. you have a floating ip

This version uses os-cloud-config to load the cloud credentials. You can
configure the appropriate cloud in host_vars/localhost. Additionally you'll
want to configure the flavor/image/etc in host_vars/localhost as well.

playbooks:
- undercloud.yml - provisionin an undercloud node and install the undercloud
- overcloud-deploy-prep.yml - loads OVB inventory, introspection and overcloud image build (DOES NOT RUN OVERCLOUD DEPLOY)

Running all at once to end up with an undercloud ready to do an 'openstack overcloud deploy':
```
ansible-playbook undercloud.yml overcloud-deploy-prep.yml --extra-vars "flavor centos version=passed-ci inventory_file_source=nodes.json"
```
