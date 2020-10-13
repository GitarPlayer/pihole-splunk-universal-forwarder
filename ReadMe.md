# Page Disambiguation

This ReadMe descripes the content of this repo. Needed dependencies and things to watch out for mainly.

## Dependencies
- [ ] Raspberry Pi with fixed IP through DHCP (configure this on your router MAC based)
- [ ] SSH enabled on all pis, it is not enabled out of the box as of 13.10.2020. simply use sudo raspi-config --> interfaces tab --> enable ssh
- [ ] Preferably a *nix machine to run Ansible on. I tested on the following environment: 
ansible 2.9.6
  config file = /etc/ansible/ansible.cfg  
  configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']  
  ansible python module location = /usr/lib/python3/dist-packages/ansible  
  executable location = /usr/bin/ansible  
  python version = 3.8.5 (default, Jul 28 2020, 12:59:40) [GCC 9.3.0]

- [ ] SSHPass installed on Ansible host(needed for passwordbased ssh connections with Ansible): Ubuntu:  
```bash
sudo apt install sshpass -y
```

- [ ] your pis must be in the authenticated users of your Ansible host (quick fix is to simply ssh into the pis and confirm that you trust them)
- [ ] you need a Splunk Cloud Trial and there you need the splunkclouduf.spl file (this file establishes trust between your pis and your cloud Splunk infrastructure)
- [ ] you need to download the Splunk Unix Addon here https://splunkbase.splunk.com/app/833/

## Usage

```bash
cd pihole-splunk-universal-forwarder
# force python3 on the pi hosts
ansible-playbook playbook.yml -e 'ansible_python_interpreter=/usr/bin/python3'
```


## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)