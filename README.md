# Ansible : Playbook Hadoop HDFS

The aim of this project is to deploy an Hadoop HDFS cluster on Vagrant Linux instance.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

What things you need to run this Ansible playbook :

*   [Vagrant](https://www.vagrantup.com/docs/installation/) must be installed on your computer
*   Update the Vagrant file based on your computer (CPU, memory), if needed
*   Update the operating system to deploy in the Vagrant file (default: Ubuntu)
*   Download the Ansible requirements:

```bash
$ ansible-galaxy install -r requirements.yml
```

### Usage

A good point with Vagrant is that you can create, update and destroy all architecture easily with some commands.

Be aware that you need to be in the Vagrant directory to be able to run the commands.

#### Deployment

This playbook has some dependencies to other roles that must be downloaded before executing the playbook :

```bash
$ ansible-galaxy install -r requirements.yml
```

This command should download the Java role from Wikitops Github account to the local role path.

To deploy the Hadoop HDFS cluster on Vagrant instances, just run this command :

```bash
$ vagrant up
```

If everything run as expected, you should be able to list the virtual machine created :

```bash
$ vagrant status

Current machine states:

hdfs01                   running (virtualbox)
hdfs02                   running (virtualbox)
hdfs03                   running (virtualbox)
```

If everything run has expected, you should access the Hadoop Web interface :
*   NameNode : http://10.0.5.11:9870/
*   Hadoop Cluster : http://10.0.5.11:8088/
*   Secondary NameNode : http://10.0.5.11:9864/
*   DataNode : http://10.0.5.11:8042/

#### Destroy

To destroy the Vagrant resources created, just run this command :

```bash
$ vagrant destroy
```

### How-To

This section list some simple command to use and manage the playbook and the Vagrant hosts.

#### Update with Ansible

To update the Hadoop HDFS cluster configuration with Ansible, you just have to run the Ansible playbook hdfs.yml with this command :

```bash
$ ansible-playbook hdfs.yml
```

#### Update with Vagrant

To update the Hadoop HDFS cluster configuration with Vagrant, you just have to run provisioning part of the Vagrant file :

```bash
$ vagrant provision
```

#### Connect to Vagrant instance

To be able to connect to a Vagrant instance, you should use the CLI which is configured to automatically use the default SSH key :

```bash
$ vagrant ssh hdfs01
```

## Author

Member of Wikitops : https://www.wikitops.io/

## Licence

This project is licensed under the Apache License, Version 2.0. For the full text of the license, see the LICENSE file.
