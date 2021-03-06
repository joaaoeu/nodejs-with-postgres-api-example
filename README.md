# Mini k8s course

Studying k8s with the [mini course](https://youtu.be/eXKg9B5ooaY) by Erick Wendel.

Project started from an example [repository](https://github.com/ErickWendel/nodejs-with-postgres-api-example).

---

# Notes: Kubernetes - k8s - minikube

pvc = persistent volume claim

```
# minikube start
# minikube dashboard
# minikube service <service_name> --url
# minikube delete

# kubectl get nodes
# kubectl get nodes -w
# kubectl get sts
# kubectl get sts -w
# kubectl get svc
# kubectl get svc -w
# kubectl get deploy
# kubectl get deploy -w
# kubectl get pod
# kubectl get pod -w

# kubectl describe nodes
# kubectl describe sts <sts_name>
# kubectl describe svc <svc_name>
# kubectl describe deploy <deploy_name>
# kubectl describe pod <pod_name>

# kubectl logs <pod_name>
# kubectl logs -f <pod_name>

# kubectl create -f file.json
# kubectl apply -f file.json

# kubectl delete -f .
# kubectl create -f .
```

---

## Node.js with Postgres Example

<img
    src="https://i.imgur.com/jUeBAiH.png"
    alt="Swagger Page of that application"
    title="Swagger Page of that application" />

### Requirements

- Node.js v8+ or Docker and Docker Compose
- Postgres running on local instance or Docker

### Running on localMachine

- Install dependencies - `npm i`
- Run project - `npm start`

### OR: Docker

- `docker-compose up`

### OR: Alternatives on pulling from Docker hub

- Docker hub image: [erickwendel/nodejs-with-postgres-api-example](https://hub.docker.com/r/erickwendel/nodejs-with-postgres-api-example/)

```shell
docker run -d -p 5432:5432 --name postgres \
    --env POSTGRES_PASSWORD=mysecretpassword \
    --env POSTGRES_DB=heroes\
    postgres
```

```shell
docker run -p 3000:3000 \
    --link postgres:postgres \
    -e POSTGRES_HOST=postgres:mysecretpassword@postgres:5432 \
    -e POSTGRES_DB=heroes \
    -e POSTGRES_SSL=false \
    erickwendel/nodejs-with-postgres-api-example:latest
```

### Viewing

- Go to swagger page - `localhost:3000/documentation`
