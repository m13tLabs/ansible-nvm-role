ansible-nvm-role
================

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-m13tlabs.nvm-660198?logo=ansible)](https://galaxy.ansible.com/ui/standalone/roles/m13tlabs/nvm/)
[![Galaxy version](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fgalaxy.ansible.com%2Fapi%2Fv1%2Froles%2F43358%2F&query=%24.summary_fields.versions%5B0%5D.name&label=version&color=blue)](https://galaxy.ansible.com/ui/standalone/roles/m13tlabs/nvm/)
[![Galaxy downloads](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fgalaxy.ansible.com%2Fapi%2Fv1%2Froles%2F43358%2F&query=%24.download_count&label=downloads&color=blue)](https://galaxy.ansible.com/ui/standalone/roles/m13tlabs/nvm/)
[![CI](https://github.com/m13tLabs/ansible-nvm-role/actions/workflows/ci.yml/badge.svg)](https://github.com/m13tLabs/ansible-nvm-role/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](https://opensource.org/licenses/MIT)

This role enrolls nvm on a machine and installs a npm module for the desired NodeJS version.

# Usage

<!-- ANSIBLE DOCSMITH MAIN START -->

## Role variables<a id="variables"></a>

Auto-generated from defaults/main.yml

The following variables can be configured for this role:

| Variable | Type | Required | Default | Description (abstract) |
|----------|------|----------|---------|------------------------|
| `nvm_dest` | `str` | No | `"{{ nvm_working_path }}/.nvm"` | Configuration value for nvm dest |
| `nvm_group` | `str` | No | `"{{ nvm_user }}"` | Group name or ID (default: '{{ nvm_user }}') |
| `nvm_node_version` | `str` | No | `"24.16.0"` | Version specification (default: '24.16.0') |
| `nvm_npm_pkgs` | `list` | No | `[]` | List of nvm npm pkgs items |
| `nvm_user` | `str` | No | `"{{ ansible_user }}"` | Username for authentication (default: '{{ ansible_user }}') |
| `nvm_version` | `str` | No | `"0.40.4"` | Version specification (default: '0.40.4') |
| `nvm_working_path` | `str` | No | `"~{{ nvm_user }}"` | File or directory path (default: '~{{ nvm_user }}') |

### `nvm_dest`<a id="variable-nvm_dest"></a>

[*⇑ Back to ToC ⇑*](#toc)

Configuration value for nvm dest

- **Type**: `str`
- **Required**: No
- **Default**: `"{{ nvm_working_path }}/.nvm"`



### `nvm_group`<a id="variable-nvm_group"></a>

[*⇑ Back to ToC ⇑*](#toc)

Group name or ID (default: '{{ nvm_user }}')

- **Type**: `str`
- **Required**: No
- **Default**: `"{{ nvm_user }}"`



### `nvm_node_version`<a id="variable-nvm_node_version"></a>

[*⇑ Back to ToC ⇑*](#toc)

Version specification (default: '24.16.0')

- **Type**: `str`
- **Required**: No
- **Default**: `"24.16.0"`



### `nvm_npm_pkgs`<a id="variable-nvm_npm_pkgs"></a>

[*⇑ Back to ToC ⇑*](#toc)

List of nvm npm pkgs items

- **Type**: `list`
- **Required**: No
- **Default**: `[]`
- **List Elements**: `str`



### `nvm_user`<a id="variable-nvm_user"></a>

[*⇑ Back to ToC ⇑*](#toc)

Username for authentication (default: '{{ ansible_user }}')

- **Type**: `str`
- **Required**: No
- **Default**: `"{{ ansible_user }}"`



### `nvm_version`<a id="variable-nvm_version"></a>

[*⇑ Back to ToC ⇑*](#toc)

Version specification (default: '0.40.4')

- **Type**: `str`
- **Required**: No
- **Default**: `"0.40.4"`



### `nvm_working_path`<a id="variable-nvm_working_path"></a>

[*⇑ Back to ToC ⇑*](#toc)

File or directory path (default: '~{{ nvm_user }}')

- **Type**: `str`
- **Required**: No
- **Default**: `"~{{ nvm_user }}"`




<!-- ANSIBLE DOCSMITH MAIN END -->
