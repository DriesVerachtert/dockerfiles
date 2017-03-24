build:
	sudo docker build -t dries/template-test .

run:
	sudo docker run -d -ti --name template-test dries/template-test

run2:
	sudo docker run -d -ti -p 11300:11300 -e MAX_JOB_SIZE=65535 --name template-test dries/template-test

stop:
	sudo docker stop template-test || true
	sudo docker rm template-test || true

clean:
	sudo docker stop template-test || true
	sudo docker rm template-test || true
	sudo docker rmi dries/template-test || true

bash:
	sudo docker exec -ti template-test bash

logs:
	sudo docker logs template-test
