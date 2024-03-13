## marka-dd-code-k8s-id637ovus



IMG := mykube-apiserver:v1.23


docker:
	cp ../../_output/local/bin/linux/amd64/kube-apiserver ./
	docker build -f Dockerfile -t ${IMG} .

scpyaml:
	-ssh l 'rm -f /etc/kubernetes/manifests/kube-apiserver.yaml'
	sleep 5
	scp kube-apiserver.yaml l:/etc/kubernetes/manifests/kube-apiserver.yaml

GOOS := linux
GOARCH := amd64
export GOOS
export GOARCH

build:
	cd /Users/hfb/projects/go/mod-pro/k8s/kubernetes && make WHAT=cmd/kube-apiserver KUBE_BUILD_PLATFORMS=linux/amd64

all: build docker scpyaml
	@echo "all"