# FPM ENV - Ansible Role
Configure the FPM environment with custom environment variables for use with PHP's `getenv('var')`

### Installation
Add this repository as a submodule of your git with:

```
git submodule add git@github.com:Vinelab/ansible-fpm-env roles/fpm-env
```

Or simply clone this repository directly into your *roles* directory:

```
git clone git@github.com:Vinelab/ansible-fpm-env roles
```

### Usage

There are 3 variables required by this role:

- `file` indicating the configuration file location
- `section` The ini section to be used when setting the variables
- `variables` an array of key-value dictionaries with:
    - `option` being the key
    - `value` is obviously the value

##### Example

```yaml
---
- hosts: web
- roles:
    -   role: fpm-env
        file: /home/user/code/env.conf
        section: website
        variables:
            - { option: AWS_ACCESS_KEY, value: DaAccessKey }
            - { option: AWS_ACCESS_SECRET, value: HumbleSecret }
```

#### Tags
All tasks have the tag `fpm-env`
