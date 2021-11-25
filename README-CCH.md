# README-CCH

## Setup
```bash
python3 --version

# virtual env
python3 -m venv .env
source .env/bin/activate
make all
```

## Launch & Test Flask app locally
```bash
python app.py

# test app locally
curl localhost:8080
curl localhost:8080/change/1/34
```

## Docker stage
```bash
# build
docker build -t flaskchange .

docker image ls
# or
docker images

docker run -p 8080:8080 flaskchange
curl localhost:8080
curl localhost:8080/change/1/34

```

## Tag & push to AWS ECR
```bash
aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin 060423150288.dkr.ecr.eu-west-1.amazonaws.com

docker tag flaskchange:latest 060423150288.dkr.ecr.eu-west-1.amazonaws.com/flaskchange:latest

docker push 060423150288.dkr.ecr.eu-west-1.amazonaws.com/flaskchange:latest
```

