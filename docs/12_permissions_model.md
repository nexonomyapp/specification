# Nexonomie — Permissions Model

## 1. Principle

Nexonomie combines collective territorial information with private project analyses.

Permissions must therefore operate at several levels.

## 2. User

A user owns or participates in projects.

## 3. Project roles

Initial roles:

```text
OWNER
EDITOR
VIEWER
```

### OWNER

Can:

- manage project members;
- edit project configuration;
- edit scenarios;
- perform analyses;
- archive the project.

### EDITOR

Can:

- edit project information;
- edit study areas;
- edit scenario information;
- add project-specific assets;
- run analyses.

### VIEWER

Can:

- view the project;
- inspect assets;
- inspect dependencies;
- view analysis results.

## 4. Collective assets

Collective assets should eventually support their own permissions.

Possible states:

```text
PUBLIC
COMMUNITY
RESTRICTED
PRIVATE
```

The first version may keep the model simpler.

## 5. Project-specific data

The following are project-specific:

- scenario;
- intervention;
- analysis;
- analysis results;
- project notes;
- project-specific validation.

These must not become visible merely because an underlying Asset is collective.

## 6. Scientific references

Scientific references may normally be shared.

However, editing authoritative reference models should eventually require elevated permissions.

Possible roles:

```text
REFERENCE_EDITOR
REFERENCE_REVIEWER
ADMIN
```

## 7. AI-generated information

Automatically generated dependencies or values should carry provenance.

The interface should make clear whether information is:

- user-entered;
- imported;
- inferred;
- AI-generated;
- scientifically validated.

AI-generated information must not automatically become authoritative scientific data.

## 8. Principle of least privilege

Users should only receive the permissions necessary for their role.

The frontend must not be the only security layer.

Server-side authorization must protect project and reference data.
