## 安装 nodejs
1. wget https://npm.taobao.org/mirrors/node/v8.9.0/node-v8.9.0.tar.gz
1. tar -xzf node-v8.9.0.tar.gz
1. cd node-v8.9.0
1. ./configure
1. make && make install
1. node --version

### 常见问题
1.WARNING: failed to autodetect C++ compiler version (CXX=g++)
> `yum install -y g++`

2.WARNING: failed to autodetect C compiler version (CC=gcc)
>`yum install -y gcc`
