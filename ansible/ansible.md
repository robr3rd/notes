# Ansible
Ansible is a server configuration management & provisioning tool.

## Coding Standards
Aside from the standards set forth by the YAML language, there aren't any kind of Coding Standards for Ansible (but there *are* various [best practices in the official docs](http://docs.ansible.com/ansible/playbooks_best_practices.html)).

As such, here I'll outline some various naming conventions that I've found useful and the least problematic:

### Capitlization
#### 
#### Handlers
- Handlers MUST be lower-case
	- Examples
		- Apache
			- `restart httpd` <-- Right!
			- `Restart httpd` <-- Wrong!
			- `Restart Httpd` <-- Wrong!
			- `Restart HTTPD` <-- Wrong!
		- iptables
			- `restart iptables` <-- Right!
			- `Restart IPTables` <-- Wrong!
			- `Restart IPtables` <-- Wrong!
			- `Restart IpTables` <-- Wrong!
			- `Restart Iptables` <-- Wrong!
			- `Restart ipTables` <-- Wrong!
		- cURL (note: I realize that this is not a service, but it demonstrates my point excellently)
			- `restart curl` <-- Right!
			- `Restart cURL` <-- Wrong! (note: Although it *does* follow the official nomenclature if you ask 3 developers how it's cased you'll get 5 answers)
			- `Restart Curl` <-- Wrong!
			- `Restart cUrl` <-- Wrong!
	- Reason
		- Unix projects have a tendency to have unpredictable naming conventions when it comes to capitalization especially (e.g. `gEdit` and perhaps more notoriously `cURL`).
		- In the spirit of consistency (especially in multi-dev environments) it's just easier to make all `handlers` lower-cased and call it a day.

## Tricky Syntax
### Register a variable from a loop and reference back to it associatively
Resutls are technically numerically-indexed dicts, so it's not obvious how to emulate associative array functionality in them.

The key is that when a variable is registered, Ansible appears to store anything present/used in the creation of that variable (such as `with_*`) in it alongside the actual output.

For instance, given the below:

```yaml
---
- vars:
  - apps:
      paths:
        app1: /path/to/foo/app1
        app2: /path/to/bar/app2

---
- name: Check the existence of application directories
  stat:
    path: "/var/www/vhosts/{{ item.value }}"
  with_dict: "{{ apps.paths }}"
  register: stat_result

- name: Copy contents for all VirtualHost sites
  copy:
    src: "vhosts/{{ item.item.value }}"
    dest: "/var/www/vhosts/{{ item.item.value }}"
  with_items: "{{ stat_result.results }}"
  when: item.stat.exists == False
  register: stat_result.results
 ```

...the value of `stat_result` would be:

```json
"stat_result": {
	"changed": false,
	"msg": "All items completed",
	"results": [
		{
			"changed": false,
			"invocation": {
				"module_args": {
					"...": "..."
				},
				"module_name": "stat"
			},
			"item": {
				"key": "app1",
				"value": "/path/to/foo/app1"
			}
		},
		{
			"changed": false,
			"invocation": {
				"module_args": {
					"...": "..."
				},
				"module_name": "stat"
			},
			"item": {
				"key": "app2",
				"value": "/path/to/bar/app2"
			}
		}
	],
	"stat": {
		"exists": true,
		"isdir": true,
		"path": "...so on so forth for `stat` results"
	}
}
```
