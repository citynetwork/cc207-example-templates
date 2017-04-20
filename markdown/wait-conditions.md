Introducing
## Wait conditions


When is a stack
# Done?


```yaml
  all_done:
    type: OS::Heat::WaitCondition
    properties:
      handle: {get_resource: all_done_handle}
      count: 1
      timeout: {get_param: timeout}

  all_done_handle:
    type: OS::Heat::WaitConditionHandle
```


Invoking WaitConditionHandles
## from CloudConfig


```yaml
  myconfig:
    type: "OS::Heat::CloudConfig"
    properties:
      cloud_config:
        package_update: true
        package_upgrade: false
        packages: { get_param: packages }
        runcmd:
          - { get_attr: ['all_done_handle', 'curl_cli'] }
```
