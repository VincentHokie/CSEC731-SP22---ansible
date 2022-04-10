# Ansible For Project C

A couple of roles created to set up a system with required services to allow running a tls termination + modsecurity proxy servers to a DVWA container.

## Getting Started

### Prerequisites

To run this project the following prerequisites are required installed and available in the enviroment.
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

### Installing

- Clone the project locally by running the following in the terminal and in your desired directory:

  `git clone git@github.com:VincentHokie/CSEC731-SP22---ansible.git`

- Navigate to the root directory of the project and run the command below to start the webserver

  `GITHUB_USER='{your-github-user}' GITHUB_TOKEN='{your-github-token}' ansible-playbook -i inventory project-c.yml`

Your github token should have the following scopes (these are the permissions on my token)

```
- repo
- admin:public_key
- user
- admin:gpg_key
```

### Assumptions

- This playbook was tested on a "fresh" Ubuntu 18 installation where the user being used was **ubuntu**. This should also work on a system with Ubuntu 20 installed with an **ubuntu** user that is part of the sudoers group, but that is not a guarantee.

### Opportunities for improvement

- Making the script compatible with more OSs
- Making less asunptions about the conditions of the server e.g. the user being used

## Authors

* [Vincent Hokie](https://github.com/VincentHokie)
