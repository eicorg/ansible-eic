EPICS Bundle
============

Install EPICS from a prebuilt downloadable RPM instead of building from source.

Example variables:

```yaml
epics_bundle_url: https://github.com/eicorg/epics-packaging/releases/download/v7.0.6-build-success/epics-bundle-7.0.6_0.0.0-2.el9.x86_64.rpm
```

Optional overrides:

```yaml
epics_bundle_filename: epics-base.rpm
epics_bundle_cleanup: true
```

Notes:

- The URL must point directly to a downloadable RPM file.
- By default the role sets `epics_bundle_disable_gpg_check: true` because ad hoc build RPMs are often unsigned.
