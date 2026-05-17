# Ideal Server Structure

This document outlines a proposed naming convention and environment layout for infrastructure across Ubuntu and Windows platforms, including backup hosts and deployment method suffixes.

---

## Environment Naming Convention

### Format

```text
<project>-<platform>[-<deployment>]-<environment>[-bk]
```

### Components

| Component | Description | Example |
|-----------|-------------|---------|
| `project` | Project or organization prefix | `fme`, `arc` |
| `platform` | Operating system | `ubu`, `win` |
| `deployment` | Deployment target | `onprem`, `cloud` |
| `environment` | Deployment environment | `dev`, `stg`, `prd` |
| `bk` | Backup / failover server designation | `-bk` |

> The deployment segment is optional for simpler naming, but adding it clarifies whether a host is on-premises or cloud-hosted.

---

## Supported Projects

| Project | Description | Supported Platforms |
|---------|-------------|---------------------|
| `fme` | Full cross-platform infrastructure | Ubuntu + Windows |
| `arc` | Windows-only infrastructure | Windows only |

---

## Environment Definitions

| Environment | Purpose |
|-------------|---------|
| `dev` | Development and testing |
| `stg` | Pre-production staging |
| `prd` | Production workloads |

---

## Platform Abbreviations

| Platform | Meaning |
|----------|---------|
| `ubu` | Ubuntu Linux |
| `win` | Windows Server |

---

## Deployment Method Abbreviations

| Method | Meaning |
|--------|---------|
| `onprem` | On-premises deployment (private datacenter or corporate infrastructure) |
| `cloud` | Cloud-hosted deployment (public or private cloud provider) |

---

# FME Infrastructure Layout

| Environment | Deployment | Ubuntu Primary | Ubuntu Backup | Windows Primary | Windows Backup |
|-------------|------------|----------------|----------------|------------------|----------------|
| Development (`dev`) | `onprem` | `fme-ubu-onprem-dev` | `fme-ubu-onprem-dev-bk` | `fme-win-onprem-dev` | `fme-win-onprem-dev-bk` |
| Development (`dev`) | `cloud` | `fme-ubu-cloud-dev` | `fme-ubu-cloud-dev-bk` | `fme-win-cloud-dev` | `fme-win-cloud-dev-bk` |
| Staging (`stg`) | `onprem` | `fme-ubu-onprem-stg` | `fme-ubu-onprem-stg-bk` | `fme-win-onprem-stg` | `fme-win-onprem-stg-bk` |
| Staging (`stg`) | `cloud` | `fme-ubu-cloud-stg` | `fme-ubu-cloud-stg-bk` | `fme-win-cloud-stg` | `fme-win-cloud-stg-bk` |
| Production (`prd`) | `onprem` | `fme-ubu-onprem-prd` | `fme-ubu-onprem-prd-bk` | `fme-win-onprem-prd` | `fme-win-onprem-prd-bk` |
| Production (`prd`) | `cloud` | `fme-ubu-cloud-prd` | `fme-ubu-cloud-prd-bk` | `fme-win-cloud-prd` | `fme-win-cloud-prd-bk` |

---

# ARC Infrastructure Layout

> Note: ARC infrastructure is Windows-only.

| Environment | Deployment | Windows Primary | Windows Backup |
|-------------|------------|------------------|----------------|
| Development (`dev`) | `onprem` | `arc-win-onprem-dev` | `arc-win-onprem-dev-bk` |
| Development (`dev`) | `cloud` | `arc-win-cloud-dev` | `arc-win-cloud-dev-bk` |
| Staging (`stg`) | `onprem` | `arc-win-onprem-stg` | `arc-win-onprem-stg-bk` |
| Staging (`stg`) | `cloud` | `arc-win-cloud-stg` | `arc-win-cloud-stg-bk` |
| Production (`prd`) | `onprem` | `arc-win-onprem-prd` | `arc-win-onprem-prd-bk` |
| Production (`prd`) | `cloud` | `arc-win-cloud-prd` | `arc-win-cloud-prd-bk` |

---

## Deployment Method Permutations

The optional deployment segment allows a clear mapping for both on-premises and cloud-hosted deployments.

| Example | Meaning |
|---------|---------|
| `fme-ubu-onprem-dev` | Ubuntu development host on-premises |
| `fme-win-cloud-stg-bk` | Windows staging backup host in the cloud |
| `arc-win-onprem-prd` | ARC Windows production host on-premises |
| `arc-win-cloud-dev-bk` | ARC Windows development backup in the cloud |

---

## Example Hostnames

### Ubuntu Production

```text
fme-ubu-onprem-prd
```

### Windows Staging Backup

```text
fme-win-cloud-stg-bk
```

### ARC Windows Production

```text
arc-win-onprem-prd
```

---

## Suggested Future Expansion

Potential additions that could scale well with this naming structure:

| Addition | Example |
|----------|---------|
| Geographic region | `fme-ubu-prd-ca` |
| Role designation | `fme-ubu-prd-db` |
| Cluster numbering | `fme-ubu-prd-01` |
| Kubernetes nodes | `fme-ubu-prd-k8s-01` |

---

## Benefits of This Structure

- Predictable and searchable hostnames
- Easy environment identification
- Clear deployment method distinction
- Consistent cross-platform naming
- Simplified automation and scripting
- Scalable for future infrastructure growth
- Easier monitoring and inventory management

---

## Recommended Best Practices

- Keep naming lowercase and hyphenated
- Avoid spaces and special characters
- Use short but recognizable abbreviations
- Reserve suffixes consistently (`-bk`, `-db`, `-web`, etc.)
- Document all reserved naming patterns
