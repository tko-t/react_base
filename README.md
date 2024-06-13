# react_base


# USAGE

```
$ mkdir app_name
$ cd app_name
$ git clone git@github.com:tko-t/react_base.git .
$ rm -rf .git
$ vi .env
  .... update .env
$ docker-compose build

$ docker-compose run --rm react npx create-react-app .
or
$ docker-compose run --rm react yarn create react-app .

# Dockerfileやらがconflictとか言い出してうまくいかなければ

$ docker-compose run --rm react npx create-react-app tmp
or
$ docker-compose run --rm react yarn create react-app tmp

$ mv tmp/* ./
$ rm -rf tmp
$ docker-compose rub --rm react yarn install
```

and push this repository

# GitHub to AWS Amplify

* Settings -> Applications -> Installed GitHub Apps -> AWS Amplify
Configure -> Repository access

# amplify.yml (Sample)

ビルドの設定

```
version: 1
frontend:
  phases:
    preBuild:
      commands:
        - cd your-app-dir # As needed
        - yarn install
    build:
      commands:
        - yarn build
  artifacts:
    baseDirectory: your-app-name/build
    files:
      - '**/*'
  cache:
    paths:
      - your-app-dir/node_modules/**/*
```

