# Bandanize Helm Charts

Kubernetes deployment charts for the full Bandanize stack.

## Components

The chart deploys the following microservices:
- **Backend**: Spring Boot API service.
- **Frontend**: Nginx serving the React SPA.
- **Postgres**: StatefulSet for the database (optional, for dev/test).

## Directory Structure

```
helm-charts/
├── charts/             # Dependency charts
│   ├── backend/        # Backend deployment & service
│   ├── frontend/       # Frontend deployment & service
│   └── postgres/       # Database configuration
├── Chart.yaml          # Main chart definition
└── values.yaml         # Global configuration values
```

## Usage

### Prerequisites
- Kubernetes Cluster (k3d, minikube, or cloud)
- Helm 3+

### Architecture details

- **Ingress**: Configured to route `api.bandanize.local` to backend and `bandanize.local` to frontend.
- **Persistence**: Using PVCs for database storage and file uploads (`/app/uploads`).

### Installation

1. Navigate to the root folder:
   ```bash
   cd helm-charts
   ```

2. Install the chart:
   ```bash
   helm install bandanize . -n bandanize --create-namespace
   ```

3. Uninstall:
   ```bash
   helm uninstall bandanize -n bandanize
   ```
