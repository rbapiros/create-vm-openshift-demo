# Fedora VM Creation and Update Playbook Demo

This repository contains an Ansible playbook to **create or update** a Fedora Virtual Machine (VM) on OpenShift Virtualization using KubeVirt.

---

## Main Playbook

- The main playbook file is [`all-in-one.yml`](./all-in-one.yml).
- This playbook handles:
  - Creating a Fedora VM with specified CPU, memory, and disk settings.
  - Adding an extra DataVolume disk if it doesn’t already exist.
  - Updating the VM’s CPU and memory configuration safely.
  - Managing VM lifecycle (stopping before updates, restarting after).

The playbook is designed to be **idempotent** — you can run it multiple times, adjusting the variables (e.g., CPU cores, RAM size), and it will update the existing VM accordingly without creating duplicates or conflicts.

---

## Archive

- The [`archive/`](./archive) folder contains older versions of this playbook.
- These versions may have different approaches or less robust handling of updates and resource version conflicts.
- Use the `all-in-one.yml` playbook for the most up-to-date and reliable behavior.

---

## Usage

1. Ensure you have access to your OpenShift cluster (eg. oc login ... )
2. Install the requirements:
   ```bash
   ansible-galaxy collection install kubernetes.core
   sudo dnf install ansible-core python3
   python3 -m ensurepip
   python3 -m pip install kubernetes
3. ansible-playbook all-in-one.yml
