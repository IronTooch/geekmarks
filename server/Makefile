.PHONY: docker-build docker-push

TAG ?= latest
FROM_TAG ?= latest

all: docker-build

docker-build:
	@echo Make - server/Makefile - Running go generate
	go generate dmitryfrank.com/geekmarks/...
        @echo Make - server/Makefile - Running go build	
	-go build --race -gcflag '-e' -i dmitryfrank.com/geekmarks/server/cmd/geekmarks-server
	@echo Make - server/Makefile - Running docker build
	docker build -t docker.io/dimonomid/geekmarks-server .
        @echo Make - server/Makefile - Removing geekmarks-server folder
	rm geekmarks-server

docker-tag:
	docker tag docker.io/dimonomid/geekmarks-server:$(FROM_TAG) docker.io/dimonomid/geekmarks-server:$(TAG)

docker-push:
	docker push docker.io/dimonomid/geekmarks-server:$(TAG)
