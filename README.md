# Proyecto Microservicio Universidades - Evaluación

Este proyecto fue desarrollado como parte de una evaluación práctica para la materia de arquitectura distribuida. Se creó un microservicio en Java (Spring Boot/Jakarta EE) conectado a una base de datos PostgreSQL, todo dockerizado y desplegado en un clúster local con Kubernetes usando Minikube.

## Contenido del Proyecto

- `Dockerfile`: para construir la imagen del microservicio.
- `docker-compose.yml`: para pruebas locales (opcional, no se usó en esta entrega).
- `k8s/`: carpeta que contiene los manifiestos de Kubernetes:
  - `database-deployment.yaml`
  - `postgres-service.yaml`
  - `microservice-deployment.yaml`
  - `universidades-service.yaml`
- Código fuente del microservicio (`.java`, `persistence.xml`, etc.).


## Instrucciones para levantar la aplicación

### 1. Clonar el repositorio

```bash
git clone https://github.com/PabloMarquez23/Prueba-sistemas
cd Prueba-sistemas
```

### 2. Iniciar Minikube

```bash
minikube start
```

### 3. Aplicar los manifiestos de Kubernetes

```bash
kubectl apply -f k8s/
```

Esto levantará:
- La base de datos PostgreSQL
- El microservicio `universidades` (3 réplicas)
- Los servicios para exponer los pods

### 4. Verificar que los pods estén funcionando

```bash
kubectl get pods
```

### 5. Acceder al microservicio

```bash
minikube service universidades-service
```

Esto abrirá el navegador automáticamente con la URL del servicio.  
Si aparece la página Whitelabel 404, significa que la app está corriendo, pero no hay endpoint definido en la raíz `/`.

Puedes probar manualmente con algo como:

```
http://127.0.0.1:PORT/api/universidades
```
