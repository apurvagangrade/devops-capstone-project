# DevOps Capstone Project

[![Build Status](https://github.com/apurvagangrade/devops-capstone-project/actions/workflows/ci-build.yaml/badge.svg)](https://github.com/apurvagangrade/devops-capstone-project/actions/workflows/ci-build.yaml)

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Python 3.9](https://img.shields.io/badge/Python-3.9-green.svg)](https://www.python.org/)

## Project Description

The DevOps Capstone Project implements an Account REST API microservice using Python and Flask. The service provides RESTful operations to create, list, read, update, and delete account records. The project demonstrates Test-Driven Development (TDD), automated testing, code coverage, code linting, containerization, and continuous integration and delivery practices.

## Objectives

- Implement REST API endpoints for account management.
- Follow Test-Driven Development principles.
- Maintain at least 95% code coverage.
- Automate linting and unit testing using GitHub Actions.
- Package the application using Docker.
- Deploy and manage the application using Kubernetes and OpenShift.
- Use Tekton pipelines to automate CI/CD workflows.

## Development Environment

This project is based on the [IBM-CD0285EN Skills Network DevOps Capstone Project](https://www.coursera.org/learn/devops-capstone-project?specialization=devops-and-software-engineering), part of the [IBM DevOps and Software Engineering Professional Certificate](https://www.coursera.org/professional-certificates/devops-and-software-engineering).

The original labs are designed to run in the IBM Developer Skills Network Cloud IDE with OpenShift.

Initialize the development environment by sourcing the setup script:

```bash
source bin/setup.sh
```

Install project dependencies:

```bash
make install
```

Start the PostgreSQL database container when required:

```bash
make db
```

Verify running containers:

```bash
docker ps
```

## Project Layout

The application follows the Model-View-Controller (MVC) pattern. The `service` package contains the microservice code, while the `tests` directory contains automated tests.

```text
├── service/
│   ├── common/
│   ├── config.py
│   ├── models.py
│   └── routes.py
├── tests/
│   ├── factories.py
│   ├── test_cli_commands.py
│   ├── test_models.py
│   └── test_routes.py
├── .github/
│   └── workflows/
├── Dockerfile
├── requirements.txt
├── setup.cfg
├── Makefile
└── README.md
```

## Account Data Model

The Account model contains the following fields:

| Field | Type | Optional |
|---|---|---|
| id | Integer | No |
| name | String(64) | No |
| email | String(64) | No |
| address | String(256) | No |
| phone_number | String(32) | Yes |
| date_joined | Date | No |

## REST API Operations

The Account REST API supports the following operations:

| Operation | HTTP Method | Endpoint |
|---|---|---|
| Create an account | POST | `/accounts` |
| List all accounts | GET | `/accounts` |
| Read an account | GET | `/accounts/{id}` |
| Update an account | PUT | `/accounts/{id}` |
| Delete an account | DELETE | `/accounts` |

These endpoints enable clients to manage account records through HTTP requests and JSON data.

## Testing and Code Quality

The project uses automated unit tests to validate application behavior. Nose is used to execute tests, while Flake8 checks Python code for style and linting issues.

Run the unit tests:

```bash
nosetests
```

Run the linter:

```bash
flake8 service tests
```

The project targets at least 95% code coverage. Automated checks help identify defects and maintain code quality throughout development.

## Continuous Integration and Delivery

GitHub Actions is used to automate code checkout, dependency installation, linting, and unit testing. Docker is used to package the application into a container image. Kubernetes and OpenShift support application deployment, while Tekton is used to define and execute pipeline tasks.

These tools demonstrate how automated testing, containerization, and deployment workflows can be integrated into a DevOps lifecycle.

## Local Kubernetes Development

For local Kubernetes development, Docker Desktop and Visual Studio Code with the Remote Containers extension can be used.

The repository provides Makefile commands for setting up the local environment:

```bash
make cluster
make tekton
make clustertasks
```

These commands are intended for the supported local development environment rather than the Cloud IDE.

## Author

Based on the IBM Skills Network DevOps Capstone Project by [John Rofrano](https://www.coursera.org/instructor/johnrofrano).

## License

This project is licensed under the Apache License 2.0. See the [LICENSE](https://github.com/apurvagangrade/devops-capstone-project/blob/main/LICENSE) file for details.
