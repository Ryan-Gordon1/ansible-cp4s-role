ansible-cp4s
=========

A role which exposes and interfaces with the Cloud Pak for Security (CP4S) Cases Rest API. The role provides you the ability to create/close cases and provides a starting point for more ansible automations by using the auth related tasks provided. 

If you have a use case you think would be good as a part of an Ansible Role, submit a PR. The hope is to build up this Role and its accompanying collection over time.

The role name to be released on Ansible Galaxy is just `cp4s` for ease of use when using in a playbook.

Requirements
------------
All the tasks in this role work entirely with either the Cloud Pak for Security Cases API or the Resilient On-Prem Rest API. 
Certain values are needed in order to make calls such as usernames, passwords and api keys. For security, it is advised to keep these values in a Ansible Vault if you plan to use these roles. 

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

## Example: Create Case


    - hosts: localhost
      gather_facts: no
      roles:
        - { role: cp4s, vars: { username: "admin@example.com", password: "Passw0rd", cp4shost: "localhost" } }

## Example: Close Case

    - hosts: localhost
      gather_facts: no
      roles:
        - {
            role: ansible-cp4s,
            vars:
              {
                username: "tester4@example.com",
                password: "Passw0rd",
                cp4shost: "localhost",
              },
          }
      vars_prompt:
        - name: "operation"
          prompt: "Enter operation to perform: (create_case, close_case)"
          private: no
        - name: "case_id"
          prompt: "Enter Case ID"
          private: no
        - name: "resolution_id"
          prompt: "Enter Case resolution ID, this is the type select value that will signal the closure reason. e.g 'Duplicate' may be ID 61 or some other ID depending on your setup"
          private: no
        - name: "resolution_summary"
          prompt: "Enter Case resolution summary, this is the message that will be used as reasoning for closing the case"
          private: no


License
-------

MIT

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
This role was developed by Ryan Gordon @ IBM. See this link for our [community forum](http://ibm.biz/resilientcommunity). Please raise a github issue with problems.
