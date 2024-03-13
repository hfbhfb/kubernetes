## marka-dd-code-k8s-id637ovus



IMG := mykube-proxy:v1.23


docker:
	cp ../../_output/local/bin/linux/amd64/kube-proxy ./
	docker build -f Dockerfile -t ${IMG} .

usehere:
	@echo "opt later"
	-ssh l 'kubectl delete -f /etc/kubernetes/debug/kube-proxy.yaml'
	# sleep 2
	scp kube-proxy.yaml l:/etc/kubernetes/debug/kube-proxy.yaml
	ssh l 'kubectl apply -f /etc/kubernetes/debug/kube-proxy.yaml'

clean:
	@echo "opt later"
	-ssh l 'kubectl delete -f /etc/kubernetes/debug/kube-proxy.yaml'


GOOS := linux
GOARCH := amd64
export GOOS
export GOARCH

build:
	cd /Users/hfb/projects/go/mod-pro/k8s/kubernetes && make WHAT=cmd/kube-proxy KUBE_BUILD_PLATFORMS=linux/amd64

all: build docker usehere
	@echo "all"