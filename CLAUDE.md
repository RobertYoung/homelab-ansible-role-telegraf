# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an Ansible role (`telegraf`) for installing and configuring the Telegraf metrics collection agent on Ubuntu/Debian systems. It configures Telegraf to send metrics to InfluxDB.

## Development Commands

### Linting
```bash
yamllint .                    # Lint all YAML files
ansible-lint                  # Lint Ansible code (currently disabled in CI)
```

### Pre-commit Hooks
```bash
pre-commit install            # Install hooks
pre-commit run --all-files    # Run all hooks manually
```

### Tool Management
Uses `mise` for tool versions (Ansible 13, pipx 1.8). Run `mise install` to set up.

## Role Structure

- `tasks/main.yml` - Installs Telegraf, configures systemd service, and sets up InfluxDB output
- `defaults/main.yml` - Default variables (service name, InfluxDB connection settings)
- `handlers/main.yml` - Handlers for restarting Telegraf and reloading systemd
- `templates/telegraf.conf.j2` - Telegraf configuration template
- `templates/telegraf.service.j2` - Systemd service unit template

## Required Variables

All variables have defaults, but you should override `telegraf_influxdb_token` with a valid InfluxDB token.

## YAML Style

Line length max 120, truthy values must be "true"/"false"/"yes"/"no", 1 space minimum after comments.
