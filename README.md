# IQ-license-offline
Use ansible and BIG-IQ license pools to license VE's in an isolated network

There are a few hard-coded references, so i'll highlight these now. Of course these can be set as variables
- Assumed BIG-IQ is configured with a license Pool
  'Key-Pool' is used in the yaml files
- IP address of the BIG-IP has been set in the j2 files
- IP address of BIG-IQ has been set in the code
- It would also be possible to create a single yaml file to run the 'assign'/'revoke', but I have kept this separate for ease of usage

To assign the license to a BIG-IP
  ansible-playbook license.yaml

To revoke the license from a BIG-IP
  ansible-playbook revoke_license.yaml

The above commands will then run a job in BIG-IQ to carry out the request. Both the above playbooks will return some diagnostic info, including the playbook command to run, to query the status of the job that has just been run, which should look similar to the below
 "ansible-playbook getStatus.yaml --extra-vars 'id=<job-id>'"


