Role Name
=========

This role enrolls nvm on a machine and installs a npm module for the desired nodeJS version.

# Usage

<!-- ANSIBLE DOCSMITH MAIN START -->

## Role variables<a id="variables"></a>

The following variables can be configured for this role:

| Variable | Type | Required | Default | Description (abstract) |
|----------|------|----------|---------|------------------------|
| `nvm_dest` | `str` | No | `"{{ nvm_working_path }}/.nvm"` | Configuration value for nvm dest |
| `nvm_group` | `str` | No | `"{{ nvm_user }}"` | Group name or ID (default: '{{ nvm_user }}') |
| `nvm_node_version` | `str` | No | `"24.16.0"` | Version specification (default: '24.16.0') |
| `nvm_npm_pkgs` | `list` | No | `[]` | List of nvm npm pkgs items |
| `nvm_user` | `str` | No | `"{{ ansible_user }}"` | Username for authentication (default: '{{ ansible_user }}') |
| `nvm_version` | `str` | No | `"0.40.4"` | Version specification (default: '0.40.4') |
| `nvm_working_path` | `path` | No | `"/home/{{ nvm_user }}"` | File or directory path (default: '/home/{{ nvm_user }}') |

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

File or directory path (default: '/home/{{ nvm_user }}')

- **Type**: `path`
- **Required**: No
- **Default**: `"/home/{{ nvm_user }}"`




<!-- ANSIBLE DOCSMITH MAIN END -->