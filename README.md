Red Hat OpenShift on Equinix Metal with GPU Worker Nodes
====

1. Install Ansible requirements: `ansible-galaxy install -r requirements.yml`
2. Create a variables file, e.g. `tmp/vars.yml`:

   ```yaml
   equinix_metal_api_key: <token>
   equinix_metal_project_id: <project>
   equinix_metal_hostname_prefix: <e.g. username>
   equinix_metal_facility: da11
   ```

3. Run `ansible-playbook sno.yml -e "@tmp/vars.yml"`