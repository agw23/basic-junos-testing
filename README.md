### Description

The script will configure a static route and configure an interface with variables you provide. Once you run the script, it will prompt you for the variables it needs. If you click 'enter' when prompted, the variables will be populated with a random IP address/next hop etc.


### Pre-requisites
* **Please make sure you have Ansible installed**. The script was tested using ansible version 2.7.5, although it should work with any. To install ansible please visit their official [website](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#intro-installation-guide) for instructions.

* Junos PyEz.
  If installing through PyPI, use the following command.
  * `sudo pip install junos-eznc`
  For other installation methods, visit [installation guide on Juniper](https://www.juniper.net/documentation/en_US/junos-pyez/topics/task/installation/junos-pyez-server-installing.html).

* The ansible-galaxy Juniper.junos module. This script uses the Juniper.junos module which is available on the galaxy website.

  * `sudo ansible-galaxy install juniper.junos`


## Inventory file

The inventory file has the IP address already listed under the [Junos] group.

**The ansible_python_interpreter variable may have to be removed, if Python path is <u>*not* </u>  /usr/local/bin/python. To check what your python path is, run `which python` from your terminal. For more information on this please visit the [ansible documentation](https://docs.ansible.com/ansible/latest/reference_appendices/interpreter_discovery.html).**

### Usage
To use this script please do the following:
1. clone the repo: `git clone https://github.com/agw23/basic-junos-testing.git`
2. navigate to the directory where you have  cloned the repo.
    `cd basic-junos-testing`
3. Run the script:
      `ansible-playbook retrieve.yaml -i inventory`

4. It will give you a series of prompt. If you skip/press 'return' or 'enter', the script will default to a bogus set of variables and configure the device with that IP/route.

### Notes

1. The script is written to run on port 40000 which is the MX. To run the script on the EX, please change the **port** variable in the retrieve.yaml file to 40001.
