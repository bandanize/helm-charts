# Bandanize Helm Charts

Bienvenido al repositorio de Helm Charts oficial para **Bandanize**. Aquí encontrarás los paquetes necesarios para desplegar la aplicación completa en Kubernetes.

## 📦 Añadir el Repositorio

Para usar estos charts, añade el repositorio a tu configuración de Helm:

```bash
helm repo add bandanize https://bandanize.github.io/helm-charts
helm repo update
```

## 🚀 Charts Disponibles

| Chart | Versión Actual | Descripción |
|-------|----------------|-------------|
| **[backend](charts/backend)** | `0.0.5` | API REST en Spring Boot (Java 17). Maneja usuarios, bandas y lógica de negocio. |
| **[frontend](charts/frontend)** | `0.0.5` | Aplicación SPA en React + Vite servida con Nginx. Incluye proxy inverso a `/api`. |
| **[postgres](charts/postgres)** | `0.1.0` | Base de datos PostgreSQL con soporte para acceso externo via Traefik (TCP/SNI). |

## 🛠️ Instalación y Uso

### Desplegar Backend
```bash
helm install backend bandanize/backend \
  --set env.SPRING_DATASOURCE_PASSWORD=tu_password \
  --set env.JWT_SECRET=tu_secreto_jwt
```

### Desplegar Frontend
```bash
helm install frontend bandanize/frontend \
  --set ingress.enabled=true \
  --set ingress.host=bandanize.local
```

### Desplegar Postgres (con Ingress TCP)
```bash
helm install postgres bandanize/postgres \
  --set postgresqlPassword=admin \
  --set ingress.enabled=true \
  --set ingress.host=postgres.bandanize.local
```

## 🤝 Contribuir
Los charts fuente se encuentran en el directorio `charts/`. Cualquier cambio pusheado a `main` disparará automáticamente la release y actualización del `index.yaml` en la carpeta `docs/`.
