# Deploy

1. Push the new changes into `master`
2. Build and push the Docker image to ECR.

    ```shell
    aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 381491955389.dkr.ecr.us-east-1.amazonaws.com
    docker build -t pdf-renderer .
    docker tag pdf-renderer:latest 381491955389.dkr.ecr.us-east-1.amazonaws.com/pdf-renderer:latest
    docker push 381491955389.dkr.ecr.us-east-1.amazonaws.com/pdf-renderer:latest
    ```

3. Go to the [Lambda](https://us-east-1.console.aws.amazon.com/lambda/home?region=us-east-1#/functions/pdf-renderer?tab=image) and deploy newly pushed image