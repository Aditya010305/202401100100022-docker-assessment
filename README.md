Practical assessment of Docker & Container Security.

## Student Details
- **Name:** Aditya Pratap Singh
- **Registration Number:** 202401100100022
- **Application Port:** 8022

## Docker Hub
- **Username:** thakuraditya135
This will be available on [Docker Hub](https://hub.docker.com/r/thakuraditya135/fest-backend) as Repository.
- **Published tags:** `1.0.0`, `1.0`, and unsigned test image `1.0.1`
- **Signed release digest (`1.0.0`):** `sha256:9164d76793b02005a0cb8a92bd0e80e81290994f6abf422e19e498367fd92384`

## Implementation Summary
Wrapped the Flask application in a Docker container.
- Deployed the frontend, backend and PostgreSQL database using Docker Compose.
- Set up a persistent database storage with a named volume.
Centrally isolated database network from the frontend network.
- Froze the backend image with a pinned Python slim base image, package upgrades and a non-root user.
- Scanned images using Trivy.
Signed image `1.0.0` with Cosign and checked its signature with `cosign.pub`.
Confirmed that the published image signed with Cosign was not signed.

## Trivy Vulnerability Comparison

| Image | CRITICAL | HIGH | Image size |
|---|---:|---:|---:|
| `fest-backend:0.1` (before hardening) | 234 | 2,243 | 1.61 GB |
| `fest-backend:0.2` (after hardening) | 0 | 44 | 331 MB |

The hardened image eliminated 234 CRITICAL vulnerabilities and 2,243 HIGH vulnerabilities to 0 and 44 respectively. It has reduced the size of its local Docker image by 1.61 GB to 331 MB.

The critical vulnerability check was successful (exit code `0`).

## Evidence and Reports
The evidence screenshots are saved in the evidence directory called screenshots/.
All trivy reports are located in the `reports/` directory.

## AI Tools Used
- Interpreted build output, Docker Compose configuration, registry timeout troubleshooting and Cosign signing and verifying commands.

## Incomplete Steps
Add to this section any missing assessment requirements.
