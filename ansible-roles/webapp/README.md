# webapp Ansible Role

Idempotent role that provisions a Linux host and deploys a web application
behind an nginx reverse proxy. Shows the patterns clients care about:
multi-OS support, handlers, Jinja2 templates, idempotency, and config
validation before applying changes.

## What it does

1. **install.yml** — creates a dedicated app user, installs nginx + logrotate
   (Debian and RedHat families), enables the service
2. **configure.yml** — removes the default vhost, renders an nginx reverse-proxy
   config from a Jinja2 template (with optional TLS block), sets up log rotation
3. **deploy.yml** — deploys a templated landing page, runs `nginx -t` to validate
   before the play finishes

## Usage

```bash
# Check mode first — shows what would change, touches nothing
ansible-playbook -i inventory/hosts site.yml --check

# Apply
ansible-playbook -i inventory/hosts site.yml
```

Override behavior with group_vars/host_vars, e.g.:

```yaml
webapp_domain: app.acme.com
webapp_port: 3000
webapp_tls_enabled: true
```

## Notes

- Handlers use `reload` (not `restart`) so config changes cause zero downtime.
- `nginx -t` runs in `deploy.yml` so a bad template never leaves the host broken.
- TLS expects certs on disk (e.g. managed by certbot); the role doesn't mint certs.
