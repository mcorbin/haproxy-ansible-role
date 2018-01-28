# HAProxy Ansible role

A simple and idempotent HAProxy role for Debian.
The first role release will be made soon.

## Installation

This role can install the latest haproxy releases from https://haproxy.debian.net/.

Important variables are (see `defaults.yml` for the default values):

`haproxy_version`: The HAProxy version
`haproxy_debian_distribution`: The Debian distribution
`haproxy_debian_backports_enabled`: Enable Debian backports
`haproxy_haproxy_backports_enabled`: Enable haproxy.debian.net backports

## Configuration

By default, this role deploy the default HAProxy configuration.

`haproxy_templates`: A list of map, each map having a `src` and `dest` key.

This role will create directory at `/etc/haproxy/haproxy.d`, and template the templates referenced in `haproxy_templates`. Then, it will assemble all the files present in `/etc/haproxy/haproxy.d` (in alphabetical order) into `/etc/haproxy/haproxy.cfg`,

This allows you to split your HAProxy configuration in multiple Ansible templates for better maintainability.

Of course, everything is idempotent ;)

The best thing to do is to define your HAProxy templates next to your playbooks, and to override the `haproxy_templates`variable to use them. Like that, you don't have to change the HAProxy role when you update your HAPrxoxy configuration.
