
```{include} ../../../roles/vault/README.md
```

## Defaults

* Domain under which
```
hs_vault_domain: "{{ public_domain }}"
hs_vault_cluster_name: "{{ hs_workspace }}"
```


* Path on the ansible controller
```
hs_vault_local_secret_dir: "{{ hs_workspace_secrets_dir }}"

hs_vault_node_name: "{{ inventory_hostname | regex_replace('_', '-') }}"
hs_vault_node_fqdn: "{{ hs_vault_node_name }}.{{ hs_vault_domain }}"

hs_vault_version: "1.12.2-1"

hs_vault_inventory_masters_group: "hashistack_masters"

hs_vault_api_protocol: "https"
hs_vault_api_address: "{{ hs_vault_node_fqdn }}"
hs_vault_api_port: "8200"
hs_vault_listen_ipv4: "{{ ansible_default_ipv4.address }}"
hs_vault_api_listener: "{{ hs_vault_listen_ipv4 }}:{{ hs_vault_api_port }}"

hs_vault_external_url: "https://vault.{{ hs_vault_domain }}"

hs_vault_cluster_protocol: "https"
hs_vault_cluster_address: "{{ hs_vault_node_fqdn }}"
hs_vault_cluster_port: "8201"
hs_vault_cluster_listener: "{{ hs_vault_listen_ipv4 }}:{{ hs_vault_cluster_port }}"
```

### Certificates

```
hs_vault_use_custom_ca: false
hs_vault_node_ca_cert: "{{ hs_vault_local_secret_dir }}/self.ca.cert.pem"
hs_vault_node_cert: "{{ hs_vault_local_secret_dir }}/self.cert.pem"
hs_vault_node_cert_private_key: "{{ hs_vault_local_secret_dir }}/self.cert.key"
hs_vault_node_cert_fullchain: "{{ hs_vault_local_secret_dir }}/self.fullchain.cert.pem"
```

### Unseal

```
hs_vault_unseal_method: "in-place"
hs_vault_unseal_key_shares: 5
hs_vault_unseal_key_threshold: 3
hs_vault_local_unseal_file: "{{ hs_vault_local_secret_dir }}/root_vault.yml"
hs_vault_local_ca_cert: "{{ hs_vault_local_secret_dir }}/ca.cert.pem"

hs_vault_terraform_work_dir: "{{ hs_workspace_tf_modules_dir }}"
