## Setting up Jenkins

~~~bash
docker pull jenkins
~~~

Run the `jenkins` container

~~~bash
docker run --rm -p 8080:8080 --name=jenkins-master jenkins
~~~

Run

~~~
docker exec (docker ps -lq) cat /var/jenkins_home/secrets/initialAdminPassword
~~~

to get the initial password

### Deamonize Jenkins

~~~
docker run -p 8080:8080 --name=jenkins-master -d \
--env JAVA_OPTS="-Xmx8192m" \
--env JENKINS_OPTS="--handlerCountStartup=100 --handlerCountMax=300" \
jenkins
~~~
