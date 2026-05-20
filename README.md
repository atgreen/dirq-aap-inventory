# dirq-aap-inventory

Minimal Ansible Automation Platform inventory source backed by a
[DirQ](https://github.com/atgreen/dirq) server.

## Usage

1. In AAP, register the `DirQ Credential` type (see the
   [collection README](https://github.com/atgreen/dirq/blob/main/collection/atgreen/dirq/README.md))
   and create a credential with your DirQ server URL and API token.
2. Create a Project that points at this repo.
3. Create an Inventory and add a source:
   - **Source**: *Sourced from a Project*
   - **Project**: the one from step 2
   - **Inventory file**: `inventory.dirq.yml`
   - **Credential**: the DirQ Credential from step 1
   - **Execution Environment**: `ghcr.io/atgreen/dirq-ee:latest`
4. Sync the source. Online DirQ agents appear as hosts, with
   `ansible_connection: atgreen.dirq.dirq` auto-set so playbooks
   reach them through the DirQ mesh instead of SSH/WinRM.

## Customizing

Edit `inventory.dirq.yml` to filter the fleet with a `query:` line or
to disable the automatic connection-plugin assignment. See the
inventory plugin docs for all options.
