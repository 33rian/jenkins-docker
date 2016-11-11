Setting up Jenkins using Docker based on [this excellent tutorial](https://github.com/maxfields2000/dockerjenkins_tutorial)

## Build images
~~~
git clone https://github.com/33rian/jenkins-docker
make build
make clean-images # remove dangling images
~~~

## Run

Just
```
make run
```
and you're good to go.

### Note
For example your domain is `example.com` and you want to serve Jenkins
on port 8080, you might need to add some configuration to `jenkins-nginx/conf/jenkins.conf`
such as

~~~
proxy_redirect http://example.com/ http://example.com:8080/;
~~~