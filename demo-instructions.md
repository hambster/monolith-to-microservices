# step 1
```
git clone https://github.com/googlecodelabs/monolith-to-microservices.git && \
cd ~/monolith-to-microservices && \
./setup.sh && \
cd ~/monolith-to-microservices/monolith && \
npm start
```

# step 2
```
cd ~/monolith-to-microservices/monolith && \  
gcloud builds submit --tag asia-east1-docker.pkg.dev/gpnr19prj0015isb-extl/gpae19afr0001isb/demo-sandbox:01 --gcs-source-staging-dir="gs://gpae19bkt0001isb-cbu-log/demo-staging" --gcs-log-dir="gs://gpae19bkt0001isb-cbu-log/demo-logs" . && \
gcloud artifacts docker images list asia-east1-docker.pkg.dev/gpnr19prj0015isb-extl/gpae19afr0001isb --include-tags | grep  demo-sandbox
```

# step 3
```
gcloud run deploy demo-sandbox \
--image="asia-east1-docker.pkg.dev/gpnr19prj0015isb-extl/gpae19afr0001isb/demo-sandbox:01" \
--port=8080 \
--platform=managed \
--service-account="gpnr19sac0004isb-run@gpnr19prj0015isb-extl.iam.gserviceaccount.com" \
--ingress=internal-and-cloud-load-balancing \
--allow-unauthenticated \
--region=asia-east1
```

# step 4
```
cd ~/monolith-to-microservices && \
vim monolith/react-app/src/pages/Home/index.js
```

# step 5
```
cd ~/monolith-to-microservices && \
./setup.sh && \
cd ~/monolith-to-microservices/monolith && \
npm start
```

# step 6
```
cd ~/monolith-to-microservices && \
gcloud builds submit --tag asia-east1-docker.pkg.dev/gpnr19prj0015isb-extl/gpae19afr0001isb/demo-sandbox:02 \
--gcs-source-staging-dir="gs://gpae19bkt0001isb-cbu-log/demo-staging" \
--gcs-log-dir="gs://gpae19bkt0001isb-cbu-log/demo-logs" .
```

# step 7
```
gcloud run deploy demo-sandbox \
--image="asia-east1-docker.pkg.dev/gpnr19prj0015isb-extl/gpae19afr0001isb/demo-sandbox:02" \
--port=8080 \
--platform=managed \
--service-account="gpnr19sac0004isb-run@gpnr19prj0015isb-extl.iam.gserviceaccount.com"\
--ingress=internal-and-cloud-load-balancing \
--allow-unauthenticated \
--region=asia-east1
```


