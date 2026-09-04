EPICS Bundle
============

Install EPICS from a prebuilt downloadable RPM instead of building from source.

Example variables:

```yaml
epics_bundle_url: https://github.com/eicorg/epics-rpm-config/releases/download/eic-7.0.10_1.0.0-2/epics-bundle-7.0.10_1.0.0-2.el9.x86_64.rpm
```

Optional overrides:

```yaml
epics_bundle_filename: epics-base.rpm
epics_bundle_cleanup: true
```

Notes:

- The URL must point directly to a downloadable RPM file.
- By default the role sets `epics_bundle_disable_gpg_check: true` because ad hoc build RPMs are often unsigned.

Molecule test with Podman
=========================

This role includes a minimal Molecule scenario at `molecule/default` that uses Podman and AlmaLinux 9.

Prerequisites:

- Podman installed and working
- Python packages for Molecule and the Podman driver
- A Linux shell or WSL environment for running Molecule
- Python 3.10+ for Ansible and Molecule

Note:

- Run Molecule from Linux or WSL with a supported Python version instead.

Install test dependencies:

```bash
python -m pip install molecule ansible-lint "molecule-plugins[podman]"
```

Run the scenario from the role directory:

```bash
cd roles/epics_bundle
molecule test
```

Useful commands:

```bash
molecule converge
molecule verify
molecule destroy
```

What the test does:

- starts an AlmaLinux 9 container with Podman
- runs this role against the container
- checks that the `epics-bundle` RPM is installed

If the package name changes, update the verify task in `molecule/default/verify.yml` to match the installed RPM name.

GitHub Actions
==============

The repository includes a workflow at `.github/workflows/molecule-epics-bundle.yml` that runs the Molecule scenario on `ubuntu-latest` with Podman.

It triggers on changes under `roles/epics_bundle/**` and the workflow file itself.

What it does:

- checks out the repository
- installs Podman and the Molecule Python dependencies
- runs `molecule test` from `roles/epics_bundle`

If you want to run the same steps locally, use the same Python packages and run `molecule test` from the role directory.
