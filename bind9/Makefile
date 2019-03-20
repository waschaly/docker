NAME = waschaly/bind9
VERSION = 0.0.2
IMAGEDIR = ./image
DOCKER = /usr/bin/docker
RM = /bin/rm
TAR = /bin/tar

.PHONY: clean build

build:
	cd $(IMAGEDIR) && \
	$(TAR) cvf named.conf.tar \
		db.178.168.192 \
		db.fritz.box \
		named.conf named.conf.local named.conf.options named.conf.default-zones
	docker build -t $(NAME):$(VERSION) --rm image

clean:
	$(RM) $(IMAGEDIR)/named.conf.tar
	$(DOCKER) container prune -f

$(IMAGEDIR)/named.conf.tar: $(IMAGEDIR)/db.178.168.192 $(IMAGEDIR)/db.fritz.box \
	$(IMAGEDIR)/named.conf $(IMAGEDIR)/named.conf.local $(IMAGEDIR)/named.conf.options \
	$(IMAGEDIR)/named.conf.default-zones
