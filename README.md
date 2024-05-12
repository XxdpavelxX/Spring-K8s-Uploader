##  Deploy
In `module1` find a simple Spring Boot application for uploading and downloading files.

Start the application using the Gradle wrapper:

```
./gradlew bootRun
```

To upload files you need pass a secret API key via the `Celonis-Auth` header, e.g. using `curl`:

```bash
curl -X POST \
  http://localhost:8080/files \
  -H 'Celonis-Auth: dev' \
  -F file=@/path/to/some/image.jpg
```

The value of this API key for local development is configured in `src/main/resources/application.yaml`.

You can download files from the application using e.g.:
```
curl -LO http://localhost:8080/files/image.jpg
```

The goal of this module is to deploy this application to Kubernetes by completing the following three tasks:

### Task 1: Dockerize
Build the application into a Docker image so it can be run in Kubernetes. Make sure to not bake any secrets into the image

### Task 2: Manifests
Write the manifests to deploy the application to a Kubernetes cluster. Try to fulfill all of the following three requirements:

* Zero-downtime deployments should be possible
* Data is persisted across application restarts
* The application should be exposed via Ingress

### Task 3: Improvements
What would you add or change to make this a fully production ready application?

# Pipeline design
Operate multiple instances (which we call _realms_) of our Intelligent Business Cloud (IBC) all around the world across multiple cloud providers. Their configuration (e.g. database hosts, connectivity to external services) is of course slightly different for each realm. What challenges can you imagine us facing in such a setup? Try to sketch a solution for maintaining and deploying into these environments as efficiently as possible.
