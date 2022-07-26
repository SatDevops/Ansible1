# ansible

This repository will have our ansible learnings and our CM of the Project.

### What is a playbook ????

```
A Playbook is a list of plays. That's why always a playbook starts as a list ( - )
```

### What is a play ?

```
A Play is a list of tasks
```

### What is a task ?

```
Any action that you want to do is called a task
    ex: Installing a package, checking the uptime of the machine , creating a user account . . .. 

``` 


### What is a fact in ansible ?

```
A Fact is nothing but a property of the target node. Before you run any playbook, ansible collects all the facts and keep it ready.

Ex: ansible all -i inventory -u centos -e ansible_password=DevOps321 -m setup

Note: Above command will show you the list of all the FACTS that your ansible is covering.
```

# ANSIBLE ROLES Helps you in :
```
1) Organising the code 
2) Increases the visibility of the code 
3) Duplicate code can be avoided 
4) Code can be re-used
5) Changes of intended actions like deletion / uptating /creation will have greater control
6) If the code is common, other teams can use your code.

Ref: https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html

```

ROLES Strcutre

```
roles/
    common/               # this hierarchy represents a "role"
        tasks/            #
            main.yml      #  <-- tasks file can include smaller files if warranted
        handlers/         #
            main.yml      #  <-- handlers file
        templates/        #  <-- files for use with the template resource
            ntp.conf.j2   #  <------- templates end in .j2
        files/            #
            bar.txt       #  <-- files for use with the copy resource
            foo.sh        #  <-- script files for use with the script resource
        vars/             #
            main.yml      #  <-- variables associated with this role
        defaults/         #
            main.yml      #  <-- default lower priority variables for this role
        meta/             #
            main.yml      #  <-- role dependencies
        <!-- library/          # roles can also include custom modules
        module_utils/     # roles can also include custom module_utils
        lookup_plugins/   # or other types of plugins, like lookup in this case -->

    webtier/              # same kind of structure as "common" was above, done for the webtier role
    monitoring/           # ""
    fooapp/               # ""

``` 
