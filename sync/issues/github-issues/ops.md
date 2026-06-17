# GitHub Issue: AuraTrip/ops — Infrastructure Setup

**Title:** `Travel planner: Terraform modules, Kubernetes manifests, and CI/CD pipelines`

**Labels:** `feature`, `infrastructure`

---

## Context

Part of the AuraTrip travel planner project. Umbrella: AuraTrip/ai-meta#TBD.

The ops repo manages infrastructure as code (Terraform, Kubernetes, GitHub Actions, AWS).

## Goal

### 1. Terraform Modules
- **api**: ECS/EKS task definition, RDS PostgreSQL (dev: single-AZ, prod: Multi-AZ), IAM roles, security groups
- **chat**: ECS/EKS service, env var injection from Secrets Manager (CLAUDE_API_KEY, AURATRAVEL_API_KEY), autoscaling
- **ui**: CloudFront + S3 or App Runner for Next.js SSR, CDN cache config
- **shared**: VPC, subnets (public/private), NAT gateway, ECR repositories for api and chat images
- Environments: `terraform/environments/dev/`, `staging/`, `prod/`

### 2. Kubernetes Manifests (`kubernetes/`)
- Namespace: `auratrip`
- Deployments: api, chat, ui — with resource requests/limits, liveness and readiness probes
- Services: ClusterIP for api and chat, LoadBalancer/Ingress for ui
- ConfigMaps: non-secret env vars per service
- HorizontalPodAutoscaler: api (2–10 replicas), chat (2–8 replicas)

### 3. GitHub Actions CI/CD
- **CI** (on PR): lint + type-check + unit tests + Docker build for api, chat, ui
- **CD** (on merge to main): build Docker image → push to ECR → deploy to staging EKS
- **Secrets**: AWS credentials via OIDC, CLAUDE_API_KEY and MAPBOX_TOKEN via AWS Secrets Manager
- Workflows live in each app repo's `.github/workflows/` (coordinated from ops)

### 4. Secrets Management
- `CLAUDE_API_KEY` — AWS Secrets Manager, injected into chat service at runtime
- `MAPBOX_TOKEN` — AWS Secrets Manager, injected into ui build
- `DATABASE_URL` — AWS Secrets Manager, injected into api service
- `JWT_SECRET` — AWS Secrets Manager, injected into api service
- Never stored in plaintext in any repo

## Pointers

- `repos/ops/` in AuraTrip/ai-meta

## Blocked on

Nothing — can start in parallel with application repos.

## Links

- Umbrella: AuraTrip/ai-meta#TBD
- Sync note: `sync/issues/2026-06-16-travel-planner.md`
- Wiki (to be updated after implementation): https://github.com/AuraTrip/ops/wiki
