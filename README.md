# Ansible For Project C

A couple of roles created to set up a system with required services to allow running a tls termination + modsecurity proxy servers to a DVWA container.

## Getting Started

### Prerequisites

To run this project the following prerequisites are required installed and available in the enviroment.
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

### Installing

- Clone the project locally by running the following in the terminal and in your desired directory:

  `git clone git@github.com:VincentHokie/CSEC731-SP22---ansible.git`


### Setup and Run for Remote Deployment

- Generate a github token that should have the following scopes (these are the permissions on my token). This will be useful later on.

```
- repo
- admin:public_key
- user
- admin:gpg_key
```

- Create a VM either locally or in a cloud provider of your choice. As you can probably tell I created my VM in AWS (based on the inventory file).

- Once the VM is ready, update the [inventory](./inventory) file by either creating a new group or using the already-existing aws group. If you create a new group, update the [project-c.yml](./project-c.yml) and replace aws with the group you added to the inventory file

- Add your IP address (public IP if using the cloud, 127.0.0.1 if using a VM on your local environment)

- Add variables required to connect to your host e.g. ansible_port, ansible_user, ansible_ssh_private_key_file in the inventory file/ using a more secure technique e.g. [ansible-vault](https://docs.ansible.com/ansible/latest/user_guide/vault.html).

- Once you are set up with the above information. Navigate to the root directory of the project and run the command below to set up the VM.

  `GITHUB_USER='{your-github-user}' GITHUB_TOKEN='{your-github-token}' ansible-playbook -i inventory project-c.yml`

- Once this has run to the end, visit port 8080 and/ or 443 of your VM to reach the DVWA container through the modsecurity and tls-termination proxies respectively.


### Assumptions

- This playbook was tested on a "fresh" Ubuntu 18 installation where the user being used was **ubuntu**. This should also work on a system with Ubuntu 20 installed with an **ubuntu** user that is part of the sudoers group, but that is not a guarantee.

### Opportunities for improvement

- Making the script compatible with more OSs
- Making less asunptions about the conditions of the server e.g. the user being used

## Authors

* [Vincent Hokie](https://github.com/VincentHokie)
