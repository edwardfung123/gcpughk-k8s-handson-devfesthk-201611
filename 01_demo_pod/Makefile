NAME=hello-node
PROJECT_ID=YOUR_PROJECT_ID
GCR=asia.gcr.io/${PROJECT_ID}/${NAME}
TAG:=$(shell /bin/date "+%Y%m%d-%H%M")

default: build

build:
	docker build -t ${NAME} .

run:
	docker run -d -p 8080:8080 --name ${NAME} ${NAME}

tag:
	docker tag -f ${NAME} $(GCR):$(TAG)
	gcloud docker push $(GCR):$(TAG)
