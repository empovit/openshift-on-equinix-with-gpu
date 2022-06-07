Red Hat OpenShift on Equinix Metal with GPU
====

Ansible playbooks for deploying a ready-to-use OpenShift cluster with GPU on Equinix Metal infrastructure.

# Pre-requisites

* An [Equinix Metal](https://metal.equinix.com/) account for provisioning a bare metal server with GPU.
* An existing Equinix Metal project where you can provision servers.
* Access to GPU-capable Equinix devices, e.g. _g2.large.x86_.
* A Red Hat account with access to [assisted installer OpenShift clusters](https://console.redhat.com/openshift/assisted-installer/clusters/~new).

# Running

1. Install Ansible requirements:
   ```sh
   ansible-galaxy install -r requirements.yml
   ```
2. Download a pull secret from https://console.redhat.com/openshift/install/pull-secret
3. Get an OpenShift offline token from https://console.redhat.com/openshift/token
4. Pick a hostname prefix to distinguish your metal devices in a shared project
5. Obtain an Equinix metal API key/token
6. Copy ID of the Equinix project you want to use
7. Create a variables file, e.g. `tmp/vars.yml`:

   ```yaml
   equinix_metal_api_key: <token>
   equinix_metal_project_id: <project>
   equinix_metal_hostname_prefix: <e.g. username>
   equinix_metal_facility: <e.g. da11>

   pull_secret_path: <e.g. tmp/pull_secret.json>
   ocm_offline_token: <offline token>
   ```

8. Run the playbook

   ```sh
   ansible-playbook sno.yml -e "@tmp/vars.yml"
   ```

# Cleaning Up

```sh
ansible-playbook sno-cleanup.yml -e "@tmp/vars.yml"
```