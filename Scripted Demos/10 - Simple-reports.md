# Simple reports

## Inventory report

    cd /vagrant/Examples/Summary-Reports
    cd inventory
    rm -fr ../results/
    ansible-playbook report.yml

    export ANSIBLE_STDOUT_CALLBACK=selective
    export ANSIBLE_CALLBACK_PLUGINS=`pwd`/../Plugins/callback/
    export ANSIBLE_SELECTIVE_LINE_LENGTH=80
    ansible-playbook report.yml

* Inspect $OUTPUT/E1.yml
* cat $OUTPUT/inventory.csv
* open $OUTPUT/inventory.html

## Uptime report

    cd framework
    rm -fr $OUTPUT
    ansible-playbook framework.yml -e dst=save

Inspect ../results/E1.yml

    ansible-playbook framework.yml -e fmt=csv -e output=uptime.csv
    ansible-playbook framework.yml \
      -e src=vars \
      -e fmt=html \
      -e output=uptime.html

## Create hosts file

    cd hosts-file
    ./cleanup.yml

Run playbook in dump mode

    ./hosts.yml --tags dump

Create and inspect the hosts file

    ./hosts.yml --tags create
    more $OUTPUT/hosts

Install the hosts file

    ./hosts.yml --tags install

