# HowTo deploy

1. Build and check container locally
```bash
sudo docker build -t app .
sudo docker run --network host -e PORT=8080 app
```

Check response on `http://localhost:8080/`
```bash
curl http://localhost:8080/
```

2. Build and push container to GCP
```bash
export PROJECT_ID=PROJECT_ID

sudo docker build -t gcr.io/${PROJECT_ID}/app:latest .
sudo docker push gcr.io/${PROJECT_ID}/app:latest
```

3. Deploy new version of the app to Cloud Run 
```bash
gcloud run deploy app --image gcr.io/${PROJECT_ID}/app:latest --region us-east4 --allow-unauthenticated
```

