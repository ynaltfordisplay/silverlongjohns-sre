# Ansible Reliability Engineering
You are an SRE responsible for managing the logs of a custom Linux systemd service called custom-monitor.service that runs on a host named sre-log-rotate. This service logs to files in /var/log/custom-monitor/, and the logs can grow rapidly.

**Your task is to create and run an Ansible playbook to automate log management using logrotate**    

The sre-log-rotate host connection details are as follows:
- Hostname: sre-log-rotate
- IPv4 address: 15.222.242.161
- Host username: ubuntu
- ssh private key: sre-logrotate-0.pem

## 🧩 Requirements 
### ✅ Log Directory + Logrotate
- Ensure /var/log/custom-monitor/ exists and has the correct permissions (0755)
- Deploy a logrotate configuration for /var/log/custom-monitor/*.log that:
    - Rotates logs daily
    - Keeps the most recent 7 days of logs
    - Compresses rotated logs
    - Skips rotation if logs are empty (0 bytes)
    - Includes a postrotate hook to reload or restart the custom-monitor.service

You may use any builtin Ansible commands (such as template, copy, or lineinfile) in the playbook.

### ✅ Before your interview
- Test and verify that everything that you implemented above works as required.
- Create a README.md with a description and instructions on how to run the playbook.
- Push all of your work to a new github public repo.  Be prepared to share the URL for that repo at the start of your interview.
- Be prepared to share your screen and demo the work in github at the start of the interview

## 🧾 Notes
- Use a single logrotate.yml playbook
- Use a single inventory.yml file, which defines the connection configuration for the sre-log-rotate host.
- You may define variables and use template files, if helpful.
- Focus on correctness, idempotency, and clear structure.
- You should include explanatory comments for each task.

