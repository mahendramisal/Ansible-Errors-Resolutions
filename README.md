# Ansible-Errors-Resolutions
Collection of issues and errors occurred in Ansible along with the solution.

Ansible is a simple and powerful automation tool, but sometimes small mistakes in configuration, inventory, or syntax can lead to confusing errors. Below are some frequently seen Ansible errors and how to fix them.

(1) "ERROR! Failed to connect to the host via ssh"

What it is:
- Ansible is unable to connect to the target server using SSH.

Possible causes:
- SSH service is not running on the target machine.
- Wrong username, password, or SSH key.
- Firewall blocking port 22.
- Incorrect host IP or hostname in inventory.

How to fix it:
- Check if you can SSH manually:
- Verify inventory file details.
- Ensure SSH service is running.
- Confirm firewall allows SSH traffic.
=====================================

(2) "ERROR! The playbook could not be found"

What it is:
- Ansible cannot find the playbook file you are trying to run.

Possible causes:
- Wrong file name.
- Wrong directory path.
- Typo in playbook name.

How to fix it:
- Check current directory using pwd.
- List files using ls.
- Make sure the playbook name is correct.
- Use full path if needed.

=====================================

(3) "ERROR! Syntax Error while loading YAML"

What it is:
- Ansible finds invalid YAML formatting in your playbook.

Possible causes:
- Wrong indentation.
- Missing : or -.
- Mixing tabs and spaces.
- Invalid YAML structure.
  
How to fix it:
- Use proper spacing (only spaces, no tabs).
- Follow correct indentation.
- Validate using:
- ansible-playbook --syntax-check playbook.yml
- Use YAML validator tools if needed.

=====================================

(4) "ERROR! Missing required arguments"

What it is:
- An Ansible module is missing mandatory parameters.

Possible causes:
- Required fields are not defined.
- Wrong module usage.
- Typo in parameter name.
  
How to fix it:
- Check module documentation.
- Verify all required parameters are present.
- Re-check spelling of arguments.

=====================================
  
(5) "UNREACHABLE! => Failed to connect"

What it is:
- Ansible marks a host as unreachable during execution.

Possible causes:
- Server is down.
- Network issue.
- Wrong IP address.
- SSH authentication failure.

How to fix it:
- Ping the server manually.
- Test SSH connectivity.
- Check inventory configuration.
- Verify network connectivity.

=====================================

(6) "ERROR! Variable is undefined"

What it is:
- Ansible is trying to use a variable that is not defined.

Possible causes:
- Variable is missing in vars file.
- Typo in variable name.
- Variable not passed properly.
- Scope issue (host/group/global).

How to fix it:
- Check variable name spelling.
- Verify variable files.
- Use debug module to print variables.
- Ensure correct variable scope.

=====================================

(7) "ERROR! No hosts matched"

What it is:
- Ansible cannot find any hosts matching the playbook target.

Possible causes:
- Wrong group name in playbook.
- Inventory file not loaded.
- Empty inventory.
- Typo in group name.

How to fix it:
- Verify inventory file.
-Run below command:
ansible-inventory --list
- Check playbook host section.
- Ensure group names match.

=====================================

(8) "ERROR! Permission denied"

What it is:
- Ansible does not have permission to perform actions on the target server.

Possible causes:
- User does not have sudo rights.
- Wrong privilege escalation method.
- Missing become: yes.
  
How to fix it:
- Enable privilege escalation:
become: yes
become_user: root
- Check sudo permissions.
- Verify user privileges.

=====================================

(9) "ERROR! Could not find or access roles"

What it is:
- Ansible cannot locate the role mentioned in the playbook.
- Possible causes:
- Role directory does not exist.
- Wrong role name.
- Roles path not configured.

How to fix it:
- Check roles folder structure.
- Verify role name.
- Update roles_path in ansible.cfg.
- Install role using below command:
ansible-galaxy install role_name

=====================================
(10) "ERROR! Module not found"

What it is:
- Ansible cannot find the specified module.

Possible causes:
- Typo in module name.
- Old Ansible version.
- Custom module path not configured.

How to fix it:
- Check module spelling.
- Upgrade Ansible if needed.
- Verify custom module path.
- Refer to official documentation.

=====================================

(11) "ERROR! Could not parse inventory"

What it is:
- Ansible cannot read or understand the inventory file.

Possible causes:
- Wrong file format.
- YAML/INI syntax errors.
- Invalid entries.

How to fix it:
- Validate inventory format.
- Check syntax.
- Test with below command:
ansible-inventory --graph

=====================================

(12) "FAILED! => Task failed"

What it is:
- A task has failed during execution.

Possible causes:
- Command error.
- Missing package.
- Service not found.
- Wrong configuration.

How to fix it:
- Check error output carefully.
- Run task manually on server.
- Enable verbose mode by using below command:
ansible-playbook playbook.yml -vvv
Debug step by step.

=====================================

(13) "ERROR! Timeout waiting for privilege escalation prompt"

What it is:
- Ansible is waiting for sudo password but not receiving it.

Possible causes:
- Wrong sudo password.
- Password prompt disabled.
- Incorrect become settings.

How to fix it:
- Run with below command:
ansible-playbook playbook.yml --ask-become-pass
- Verify sudo configuration.
- Check become parameters.
