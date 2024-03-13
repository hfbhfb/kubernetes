
cptodevice:
	ssh l 'systemctl stop kubelet;'
	scp ../../_output/local/bin/linux/amd64/kubelet l:/usr/bin/mykubelet123a


usehere: cptodevice
	@echo "usehere"
	scp 10-kubeadm.conf l:/usr/lib/systemd/system/kubelet.service.d/10-kubeadm.conf
	ssh l 'systemctl daemon-reload; systemctl start kubelet;'



recover: 
	@echo "usehere"
	scp old10-kubeadm.conf l:/usr/lib/systemd/system/kubelet.service.d/10-kubeadm.conf
	ssh l 'systemctl daemon-reload; systemctl restart kubelet;'


clean:
	@echo "clean"

GOOS := linux
GOARCH := amd64
export GOOS
export GOARCH

# 	cd /Users/hfb/projects/go/mod-pro/k8s/kubernetes && CGO_ENABLED=0 GOOS=linux go build -tags netgo -ldflags '-extldflags "-static" -X main.gitVersion=v1.23.4' -o mykubelet123 cmd/kubelet/kubelet.go
build:
	cd /Users/hfb/projects/go/mod-pro/k8s/kubernetes && make WHAT=cmd/kubelet KUBE_BUILD_PLATFORMS=linux/amd64

all: build usehere
	@echo "all"