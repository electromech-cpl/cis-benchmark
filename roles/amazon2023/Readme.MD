```markdown
# Ansible CIS Benchmark Role

This Ansible role implements security configurations based on the CIS (Center for Internet Security) Benchmark for Ubuntu servers. It is compatible with Ansible versions 2.12.0 and above.

## Configuration

You can configure variables in `defaults/main.yml`.


### EC2 Pipeline

The role includes settings for running in an EC2 pipeline:

```yaml
system_is_ec2: true
```

This variable is used to skip events in the EC2 instance testing pipeline.

## Usage

### Running Specific CIS Security Levels

To apply a specific CIS security level, navigate to the `foldername/` directory and execute the playbook with the desired tag. For example, to apply level 1 security configurations:

```bash
ansible-playbook playbook.yml --tags=amazon2023-level1-server
```

### Applying Both CIS Levels

To apply both level 1 and level 2 CIS security configurations, navigate to `foldername/roles/amazon2023/` directory and run the main playbook:

```bash
cd foldername/roles/amazon2023
ansible-playbook main.yml
```
## Role Variables
This role is designed that the end user should not have to edit the tasks themselves. All customizing should be done by overriding the required varaibles as found in defaults/main.yml file. e.g. using inventory, group_vars, extra_vars
## Technical Dependencies:

Python3
Ansible 2.10+
python3-libselinux (installed in prereqs if required)
collections found in collections/requirements.yml
pre-commit is available if installed on your host for pull request testing.

## Local Testing
Ansible

ansible-base 2.10.17 - python 3.8
ansible-core 2.13.4 - python 3.10
ansible-core 2.15.1 - python 3.11
## Note

I have commented setting root password in tasks/main.yml, if you want to configure it you can uncomment it.


This script will enable Selinux for you

This role will make changes to the system which may have unintended consequences. This is not an auditing tool but rather a remediation tool to be used after an audit has been conducted.

Check Mode is not supported! The role will complete in check mode without errors, but it is not supported and should be used with caution. A compliance scanner should be used for compliance checking over check mode.

This role was developed against a clean install of the Operating System. If you are implementing to an existing system please review this role for any site specific changes that are needed.

To use the release version, please point to the main branch and relevant release for the cis benchmark you wish to work with.

## Contributions

Contributions are welcomed! Please submit any improvements or suggestions via pull requests.

## License

This project is licensed under the [MIT License](LICENSE).
```

This README provides comprehensive information about the Ansible CIS Benchmark role, including configuration options, usage guidelines for specific CIS security levels, notes, contribution guidelines, and licensing information. Additionally, it emphasizes the compatibility of the role with Ansible versions 2.12.0 and above.