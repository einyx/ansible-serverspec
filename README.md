# ansible-serverspec

ansible-serverspec is an Ansible role. Use this role to install [ServerSpec](http://serverspec.org/).

## Provides

* Ruby(default 2.0.0-p645)
* Bundler
* ServerSpec

## Requires

1. Ansible(checked 1.9.1)
2. CentOS 6.5 later
3. Vagrant(optional)

## Usage

### Get the code
`$ git clone https://github.com/uzresk/ansible-serverspec.git`

### create hosts file 

	[server]  
	192.168.1.20  

### Create Playbook

    - hosts: server
      become: yes
      roles:
        - serverspec

### Run the Playbook

`$ ansible-playbook -i hosts site.yml`

### Example Output

	[vagrant@ansible-host ansible-serverspec]$ ansible-playbook -i hosts site.yml

	PLAY [server] *****************************************************************

	GATHERING FACTS ***************************************************************
	ok: [192.168.1.20]

	TASK: [selinux | Download EPEL Repo - Centos/RHEL 6] **************************
	changed: [192.168.1.20]

	TASK: [selinux | Install EPEL Repo - Centos/RHEL 6] ***************************
	changed: [192.168.1.20]

	TASK: [selinux | Download EPEL Repo - Centos/RHEL 7] **************************
	skipping: [192.168.1.20]

	TASK: [selinux | Install EPEL Repo - Centos/RHEL 7] ***************************
	skipping: [192.168.1.20]

	TASK: [selinux | Install libselinux-python] ***********************************
	changed: [192.168.1.20]

	TASK: [serverspec | install library] ******************************************
	changed: [192.168.1.20] => (item=git,gcc,gcc-c++,make,patch,readline-devel,zlib-devel,libyaml-devel,openssl-devel)

	TASK: [serverspec | git clone ruby-build] *************************************
	changed: [192.168.1.20]

	TASK: [serverspec | ruby-build-check] *****************************************
	ok: [192.168.1.20]

	TASK: [serverspec | ruby-build] ***********************************************
	changed: [192.168.1.20]

	TASK: [serverspec | setting path] *********************************************
	changed: [192.168.1.20]

	TASK: [serverspec | bundler install check] ************************************
	ok: [192.168.1.20]

	TASK: [serverspec | install bundler] ******************************************
	changed: [192.168.1.20]

	TASK: [serverspec | create serverspec directory] ******************************
	changed: [192.168.1.20]

	TASK: [serverspec | copy Gemfile] *********************************************
	changed: [192.168.1.20]

	TASK: [serverspec | serverspec install check] *********************************
	ok: [192.168.1.20]

	TASK: [serverspec | install bundler] ******************************************
	changed: [192.168.1.20]

	PLAY RECAP ********************************************************************
	192.168.1.20               : ok=15   changed=11   unreachable=0    failed=0

