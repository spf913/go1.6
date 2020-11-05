# go1.6
# Install go
wget https://golang.org/dl/go1.6.linux-amd64.tar.gz
tar -C /usr/local -xzf /tmp/go1.6.linux-amd64.tar.gz

ln -s /usr/local/go/bin/go /usr/bin/go
ln -s /usr/local/go/bin/go /usr/local/bin/go
ln -s /usr/local/go/bin/godoc /usr/local/bin/godoc
ln -s /usr/local/go/bin/gofmt /usr/local/bin/gofmt
whereis go

# Add it to your PATH
export GOPATH=/gopath
export PATH=$PATH:$GOPATH/bin:/usr/local/bin:/usr/local/go/bin/

go version


# Get kubernetes source code
git clone --depth 1 https://github.com/spf913/kube-mesos-framework.git

# Add kubernetes source code to GOPATH
git clone https://github.com/spf913/kube-mesos-framework.git $GOPATH/src/k8s.io/kubernetes
cd $GOPATH/src/k8s.io/kubernetes

# Build Binary
export KUBERNETES_CONTRIB=mesos
make
make  test
