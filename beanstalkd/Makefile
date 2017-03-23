build:
	sudo docker build -t dries/beanstalkd .

run:
	sudo docker run -d -ti -p 11300:11300 -v /var/lib/beanstalkd:/srv/beanstalkd --name beanstalkd dries/beanstalkd

run2:
	sudo docker run -d -ti -p 11300:11300 -e MAX_JOB_SIZE=65535 --name beanstalkd dries/beanstalkd

stop:
	sudo docker stop beanstalkd || true
	sudo docker rm beanstalkd || true

clean:
	sudo docker stop beanstalkd || true
	sudo docker rm beanstalkd || true
	sudo docker rmi dries/beanstalkd || true

bash:
	sudo docker exec -ti beanstalkd bash

logs:
	sudo docker logs beanstalkd
