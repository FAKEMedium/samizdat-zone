# Samizdat-Plugin-Zone

DNS zone management (PowerDNS) for Samizdat. An **offerable** Samizdat module (clonable/hostable; can be offered to
customers). Extracted from the Samizdat monorepo with history; installs as a
standalone CPAN/pkg distribution.

## Layout

    lib/Samizdat/Plugin/Zone.pm        routes + helper
    lib/Samizdat/Controller/Zone.pm    request handlers
    lib/Samizdat/Model/Zone.pm         business logic / data access
    lib/Samizdat/resources/templates/zone/   views (install to site_perl)
    lib/Samizdat/resources/locale/zone/      per-module translations

Resources install under `site_perl/Samizdat/resources/...`, where the core
resolver (`$app->resource(...)`) finds them.

## Dependencies

- **Samizdat** (core) — provides `Samizdat::Model::Cache` and the resource
  resolver. Not yet on CPAN; install the core dist or put it on `PERL5LIB`.
- Mojolicious.

## Install

    perl Makefile.PL
    make && make test          # core (Samizdat) must be on PERL5LIB
    make install               # or: make install INSTALL_BASE=/path/to/prefix

Enable it in `samizdat.yml` via `extraplugins: [Zone]`.
