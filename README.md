# VM Creation and Update Playbook Demo

This repository contains an Ansible playbook to **create or update** a Virtual Machine (VM) on OpenShift Virtualization using KubeVirt.

---

## Main Playbooks

- The main playbook files are create_vm.yml[`create_vm.yml`](./create_vm.yml) and [`update_vm_resources_and_add_disk.yml`](./update_vm_resources_and_add_disk.yml)
- create_vm.yml handles:
  - Creating a VM with specified CPU, memory, and disk settings.
- update_vm_resources_and_add_disk.yml handles:
  - Adding an extra DataVolume disk if it doesn’t already exist.
  - Updating the VM’s CPU and memory configuration safely.
- all-in-one.yml does all of the above, in a single playbook.

The playbooks are designed to be **idempotent** — you can run it multiple times, adjusting the variables (e.g., CPU cores, RAM size), and it will update the existing VM accordingly without creating duplicates or conflicts.

---

## Archive

- The [`archive/`](./archive) folder contains older versions of this playbook.
- These versions may have different approaches or less robust handling of updates and resource version conflicts.
- Use the `all-in-one.yml` playbook for the most up-to-date and reliable behavior.

---

## Usage

1. Ensure you have access to your OpenShift cluster
   ```bash
   oc login ...
3. Install the requirements:
   ```bash
   sudo dnf install ansible-core python3
   ansible-galaxy collection install kubernetes.core
   python3 -m ensurepip
   python3 -m pip install kubernetes
3. Clone the repository
4. Run the playbook:
   ```bash
   ansible-playbook all-in-one.yml
