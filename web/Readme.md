# Howto deploy 

1. Build the project
```bash
npm run build
```

2. Copy the files from the `dist` folder to the bucket
```bash

export BUCKET_NAME=your-bucket-name
gsutil -m cp -r dist/* gs://${BUCKET_NAME}

```

3. Set the bucket as public
```bash
gsutil iam ch allUsers:objectViewer gs://${BUCKET_NAME} 
```
