# Ansible Role: RabbitMQ

Installs RabbitMQ service on RHEL/CentOS.
RabbitMQ is an open-source message-broker software that originally implemented the Advanced Message Queuing Protocol (AMQP). 
Currently this role provides a possibility to install RabbitMQ server and create virtualhosts and users. 

## Requirements

This role requires installed Erlang. Please check version requirenments on [Which Erlang](https://www.rabbitmq.com/which-erlang.html) page.
An example of installation:

    cd ~ && wget https://packages.erlang-solutions.com/erlang/rpm/centos/7/x86_64/esl-erlang_23.3.1-1~centos~7_amd64.rpm
    sudo yum -y install esl-erlang_23.3.1-1~centos~7_amd64.rpm


## Role Variables

An example of configuration:

    use_classyllama_rabbitmq: true
    rabbitmq_vhosts:
      - name: production
      - name: staging
    rabbitmq_users:
      - user: production
        password: changeme
        vhost: production
      - user: staging
        password: changeme
        vhost: staging
      - user: manager
        password: rabbitmqmgr
        tags: management

See `defaults/main.yml` for details.

## Dependencies

* `classyllama.rabbitmq`

## Example Playbook

    - hosts: all
      roles:
         - { role: classyllama.rabbitmq, tags: rabbitmq, when: use_classyllama_rabbitmq | default(false) }

## License

This work is licensed under the MIT license. See LICENSE file for details.
