🔭 Architecture (at a glance)

VPC with public subnets (ALB) and private subnets (Fargate tasks) across 2 AZs
ECR repos for each service
ECS Fargate cluster + services (one service per microservice)
ALB with path-based routing:

/patients → Patient Service
/appointments → Appointment Service

CloudWatch Logs for container logs
S3 backend for Terraform remote state + DynamoDB table for locking
GitHub OIDC to assume AWS IAM role (no long-lived secrets)
GitHub Actions:

IaC workflow: fmt, validate, plan on PR; apply on merge to main
App CI/CD: build & push images to ECR; force ECS deployment
