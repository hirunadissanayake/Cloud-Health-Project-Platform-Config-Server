# Config-Server

Centralized external configuration server for the Cloud Health microservices ecosystem. It supports a native local repository and a Git-backed production repository.

## About

This project is part of the Cloud Health Project for ITS 2130 Enterprise Cloud Architecture. Every platform and domain service imports its environment-neutral configuration from this server during startup.

## Tech Stack

| Technology | Details |
|---|---|
| Java | 25 |
| Spring Boot | 4.1.0 |
| Spring Cloud | 2025.1.2 |
| Spring Cloud Config Server | Native and Git configuration backends |
| Spring Boot Actuator | Health and readiness endpoints |
| Maven Wrapper | Reproducible builds |

## Configuration Layout

The external repository contains:

```text
config-repository/
├── application.yml
├── api-gateway.yml
├── discovery-server.yml
├── patient-service.yml
├── diagnostics-service.yml
└── file-service.yml
```

Local mode reads `../config-repository`. Production mode clones the repository configured through `CONFIG_GIT_URI`.

## Service Details

| Property | Value |
|---|---|
| Port | `8888` |
| Artifact ID | `config-server` |
| Group ID | `com.cloudhealth` |
| Default profile | `native` |
| Production profile | `git` |
| Repository | `Cloud-Health-Project-Platform-Config-Server` |

## Getting Started

> **Important:** Config-Server starts first because all other services depend on it.

```bash
./mvnw spring-boot:run
```

Verify a served configuration:

```text
http://localhost:8888/api-gateway/default
```

For the Git-backed profile:

```bash
export SPRING_PROFILES_ACTIVE=git
export CONFIG_GIT_URI=https://github.com/YOUR_USERNAME/Cloud-Health-Project-Platform-Config-Repository.git
export CONFIG_GIT_BRANCH=main
./mvnw spring-boot:run
```

## Testing

```bash
./mvnw test
```

## Project Details

| Property | Value |
|---|---|
| Student | Hiruna Dissanayake |
| Student number | `241711024` |
| GCP project | `cloud-health-506015-hiruna` |
