NAME = waschaly/puppet
VERSION = 0.0.1
DOCKER = docker

.PHONY: build

build:
	$(DOCKER) build -t $(NAME):$(VERSION) .

release: build
