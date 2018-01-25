# sansible_aws_dynamo_db

Master: [![Build Status](https://travis-ci.org/sansible/sansible_aws_dynamo_db.svg?branch=master)](https://travis-ci.org/sansible/sansible_aws_dynamo_db)
Develop: [![Build Status](https://travis-ci.org/sansible/sansible_aws_dynamo_db.svg?branch=develop)](https://travis-ci.org/sansible/sansible_aws_dynamo_db)

* [ansible.cfg](#ansible-cfg)
* [Installation and Dependencies](#installation-and-dependencies)
* [Tags](#tags)
* [Examples](#examples)

This role provisions a Dynamo DB table via Cloudformation.




## Installation and Dependencies

To install run `ansible-galaxy install sansible.aws_dynamo_db` or add this to your
`roles.yml`.

```YAML
- name: sansible.aws_dynamo_db
  version: v1.0
```

and run `ansible-galaxy install -p ./roles -r roles.yml`




## Tags

This role uses tags: **build** and **assert**

* `build` - Provisions a Dynamo DB table
* `assert` - Checks that the JSON template used for CloudFormation is valid




## Examples

Simply this include role in your playbook, required variables for a Dynamo DB
table are available from the [AWS Docs](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-dynamodb-table.html):

```YAML
- name: Install and configure sansible_aws_dynamo_db
  hosts: "somehost"

  roles:
    - role: sansible.aws_dynamo_db
      sansible_aws_dynamo_db_attribute_definitions:
        - name: "name"
          type: "S"
        - name: "value"
          type: "S"
      sansible_aws_dynamo_db_key_schema:
        - name: "name"
          key_type: "HASH"
      sansible_aws_dynamo_db_provisioned_throughput_read: 1
      sansible_aws_dynamo_db_provisioned_throughput_write: 1
      sansible_aws_dynamo_db_region: eu-west-1
      sansible_aws_dynamo_db_stack_name: "test-dynamo-db"
      sansible_aws_dynamo_db_table_name: "test-dynamo-db"
      sansible_aws_dynamo_db_tags:
        Name: "test-dynamo-db"
```

## Dry run

You can generate and show the CF template only by using the dry run variable
like so:

```YAML
- name: Install and configure sansible_aws_dynamo_db
  hosts: "somehost"

  roles:
    - role: sansible.aws_dynamo_db
      sansible_aws_dynamo_db_attribute_definitions:
        - name: "name"
          type: "S"
        - name: "value"
          type: "S"
      sansible_aws_dynamo_db_key_schema:
        - name: "name"
          key_type: "HASH"
      sansible_aws_dynamo_db_dry_run: no
      sansible_aws_dynamo_db_provisioned_throughput_read: 1
      sansible_aws_dynamo_db_provisioned_throughput_write: 1
      sansible_aws_dynamo_db_region: eu-west-1
      sansible_aws_dynamo_db_stack_name: "test-dynamo-db"
      sansible_aws_dynamo_db_table_name: "test-dynamo-db"
      sansible_aws_dynamo_db_tags:
        Name: "test-dynamo-db"
```
