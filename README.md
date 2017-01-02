# docker-angular-cli
This is a basic Docker image which allows you to create a dev env for your AngularJS 2 projects.
It only contains Node, Git, and angular-cli.
Every other libraries must be installed using your project's package.json or bower.json.

For AngularJS purpose, you can use the 'tutorial' below...

## Installation:
### Build image
```sh
$ docker build -t "cdue/docker-angular-cli:latest" .
```

### Or get it from the Docker Hub
```sh
$ docker pull "cdue/docker-angular-cli"
```

## Run a bash:
```sh
$ docker run --rm -it -v $(pwd):/app/ -p 4200:4200 -p 49153:49153 "cdue/docker-angular-cli:latest"
```
Windows users must add a / before $(pwd)

## Create a new angularjs 2 project
After you ran a bash using the above docker command, run:
```sh
$ ng new my-angular-project
```
Exit from your bash.

As the bash is using root user, you'll need to change your project folder owner
```sh
$ sudo chown -R your_user:your_group my-angular-project
```

## Serving your angularjs 2 project
Go to your project folder:
```sh
$ cd my-angular-project
```

Then run a bash using the above docker command:
```sh
$ ng serve --host 0.0.0.0 [--port 4200 --live-reload-port 49153]
```
**Note that you should use this 'ng serve --host ...' command because 'ng serve' simple command won't work properly** (the part included between [] is optional).

## Other angular-cli commands
If you want to know more about angular-cli, such as how to generate a new Component, a new Directive, or anything else, just go to https://cli.angular.io/.
