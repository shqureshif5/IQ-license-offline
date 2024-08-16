# IQ-license-offline
Use ansible and BIG-IQ license pools to license VE's in an isolated network. Derived from https://clouddocs.f5.com/products/big-iq/mgmt-api/v6.0/HowToSamples/bigiq_api_modules/t_license_member_management.html#supported-license-types

There are a few hard-coded references, so i'll highlight these now. Of course these can be set as variables
- Assumed BIG-IQ is configured with a license Pool. 'Key-Pool' is used in the yaml files
- For simplicity in my lab the BIG-IQ and BIG-IP had the same username/password - obviously not ideal in production
- IP address of the BIG-IP has been set in the j2 files
- IP address of BIG-IQ has been set in the code
- It would also be possible to create a single yaml file to run the 'assign'/'revoke', but I have kept this separate for ease of usage

To assign the license to a BIG-IP

  ansible-playbook license.yaml

To revoke the license from a BIG-IP

  ansible-playbook revoke_license.yaml

The above commands will then run a job in BIG-IQ to carry out the request. Both the above playbooks will return some diagnostic info, including the playbook command to run, to query the status of the job that has just been run, which should look similar to the below

 "ansible-playbook getStatus.yaml --extra-vars 'id=<job-id>'"


