Perfect! Now let's build and push all the other services using the same approach.

## **Build and Push All Services:**

```powershell
cd C:\Users\Administrator\Downloads\GratitudeApp-k8s

# API Gateway
docker build -f services/api-gateway/Dockerfile -t us-central1-docker.pkg.dev/heroviredacademics/prince-repo/api-gateway:latest .
docker push us-central1-docker.pkg.dev/heroviredacademics/prince-repo/api-gateway:latest

# Entries Service
docker build -f services/entries-service/Dockerfile -t us-central1-docker.pkg.dev/heroviredacademics/prince-repo/entries-service:latest .
docker push us-central1-docker.pkg.dev/heroviredacademics/prince-repo/entries-service:latest

# Moods API
docker build -f services/moods-api/Dockerfile -t us-central1-docker.pkg.dev/heroviredacademics/prince-repo/moods-api:latest .
docker push us-central1-docker.pkg.dev/heroviredacademics/prince-repo/moods-api:latest

# Moods Service
docker build -f services/moods-service/Dockerfile -t us-central1-docker.pkg.dev/heroviredacademics/prince-repo/moods-service:latest .
docker push us-central1-docker.pkg.dev/heroviredacademics/prince-repo/moods-service:latest

# Server Main
docker build -f services/server-main/Dockerfile -t us-central1-docker.pkg.dev/heroviredacademics/prince-repo/server-main:latest .
docker push us-central1-docker.pkg.dev/heroviredacademics/prince-repo/server-main:latest

# Stats API
docker build -f services/stats-api/Dockerfile -t us-central1-docker.pkg.dev/heroviredacademics/prince-repo/stats-api:latest .
docker push us-central1-docker.pkg.dev/heroviredacademics/prince-repo/stats-api:latest

# Stats Service
docker build -f services/stats-service/Dockerfile -t us-central1-docker.pkg.dev/heroviredacademics/prince-repo/stats-service:latest .
docker push us-central1-docker.pkg.dev/heroviredacademics/prince-repo/stats-service:latest

# Client
docker build -f client/Dockerfile -t us-central1-docker.pkg.dev/heroviredacademics/prince-repo/client:latest client/
docker push us-central1-docker.pkg.dev/heroviredacademics/prince-repo/client:latest
```

## **Or run them all in a loop:**

```powershell
foreach ($svc in @("api-gateway", "entries-service", "moods-api", "moods-service", "server-main", "stats-api", "stats-service")) {
    Write-Host "`nBuilding and pushing $svc..." -ForegroundColor Cyan
    docker build -f "services/$svc/Dockerfile" -t "us-central1-docker.pkg.dev/heroviredacademics/prince-repo/${svc}:latest" .
    docker push "us-central1-docker.pkg.dev/heroviredacademics/prince-repo/${svc}:latest"
}

# Client
Write-Host "`nBuilding and pushing client..." -ForegroundColor Cyan
docker build -f client/Dockerfile -t us-central1-docker.pkg.dev/heroviredacademics/prince-repo/client:latest client/
docker push us-central1-docker.pkg.dev/heroviredacademics/prince-repo/client:latest
```

## **Verify all images:**

```powershell
gcloud artifacts docker images list us-central1-docker.pkg.dev/heroviredacademics/prince-repo
```

Just copy and paste the loop command and it will build and push all 8 images! 🚀