# Ansible Role: Elasticsearch [![Build Status](https://travis-ci.org/jradtilbrook/ansible-role-elasticsearch.svg?branch=master)](https://travis-ci.org/jradtilbrook/ansible-role-elasticsearch)

This role installs and configures Elasticsearch 5.x for the Elastic stack.

It has only been designed to work on Ubuntu 16.04, but other Debian flavours
should also work.


## Requirements

None.


## Role Variables

`elasticsearch_config_settings` is a YAML dictionary used to fully configure
Elasticsearch. The contents of this variable are written the configuration file
in YAML format. Therefore, it accepts any valid configuration property supported
by Elasticsearch.

`elasticsearch_jdk_version` is the JDK package to install that Elasticsearch
will run on. The default is OpenJDK but you could also use Oracle.

There are also `elasticsearch_jvm_heap_min` and `elasticsearch_jvm_heap_max`
settings you can use to change the JVM heap allocated to Elasticsearch. They
default to 2GB. Note that the Elasticsearch documentation states you should set
these to the same value.

If you are using this role and need extra configuration of the JVM or Log4j,
make a PR to add the setting and I'll be more than happy to accept it - I just
have no need for other settings at this time.

`elasticsearch_install_state`: This is useful for updating Elasticsearch to
newer versions after it has already been installed. Use `latest` to achieve this
functionality.


## Resources

Documentation related to Elasticsearch can be found at the links below:

- [documentation](https://www.elastic.co/guide/en/elasticsearch/reference/5.3/index.html)


## Dependencies

None, but you might also want Kibana to visualise the data ingested into Elasticsearch.
See my [jradtilbrook.kibana](https://github.com/jradtilbrook/ansible-role-kibana) role.

Check out my other roles on [Ansible Galaxy](https://galaxy.ansible.com/jradtilbrook)
if you are installing the entire Elastic Stack.


## Example Playbook

```yaml
- hosts: servers
  become: yes

  roles:
    - role: jradtilbrook.elasticsearch
```


## License

MIT
