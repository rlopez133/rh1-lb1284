# Ticket Enrichment Demo — Setup Requirements

Everything that needs to be in place before the end-to-end flow works.

---

## AAP (Ansible Automation Platform)

### Job Templates

- [ ] **Incidents | Update Ticket** — runs `notify_openflake.yml`
- [ ] **Simulate Ticket Enrichment** — runs `openflake-incidient-simulate.yml`

### Custom Credential Types

- [ ] **AO Token** — injects `AO_CLIENT_ID` and `AO_CLIENT_SECRET` as env vars
- [ ] **OpenFlake** — injects `openflake_instance_url`, `openflake_username`, `openflake_password` as extra_vars *and* `OPENFLAKE_INSTANCE_URL`, `OPENFLAKE_USERNAME`, `OPENFLAKE_PASSWORD` as env vars

### Credential Assignments

- [ ] **Simulate Ticket Enrichment JT** requires:
  - AO Token credential
  - OpenFlake credential
  - OCP Token credential
  - VM credential (SSH to target host for Play 1 — plants fake issues on the box)
- [ ] **Incidents | Update Ticket JT** requires:
  - OpenFlake credential

---

## Ansible Orchestrator (AO)

- [ ] Service Account creation (provides the `ao_sa_client_id` / `ao_sa_client_secret`)
- [ ] OpenFlake MCP Server connected
- [ ] AAP MCP Server connected
- [ ] qwen3 model configured for the AI agents (triage, enrich & assign)

---

## OpenShift (OCP)

- [ ] OpenFlake app deployed
- [ ] OpenFlake MCP server deployed
- [ ] `ALLOW_HOST` env var set to permit OpenFlake access

---

