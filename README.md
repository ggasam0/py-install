# Python 3.13.7 编译安装步骤

### 1. 下载源码

```bash
wget https://www.python.org/ftp/python/3.13.7/Python-3.13.7.tgz
tar -zxvf Python-3.13.7.tgz
cd Python-3.13.7
```

---

### 2. 安装依赖

```bash
sudo apt-get update
sudo apt-get install -y \
    build-essential \
    libssl-dev zlib1g-dev \
    libncurses5-dev libncursesw5-dev \
    libreadline-dev libsqlite3-dev \
    libgdbm-dev libdb5.3-dev \
    libbz2-dev libexpat1-dev liblzma-dev \
    tk-dev libffi-dev uuid-dev \
    ca-certificates
```

---

### 3. 配置编译参数

```bash
./configure --prefix=/usr/local/python3.13 \
    --enable-optimizations \
    --with-ensurepip=install \
    --enable-shared \
    --with-system-ffi \
    --with-computed-gotos \
    --enable-loadable-sqlite-extensions
```

---

### 4. 编译与安装

```bash
make -j$(nproc)     # 并行编译，速度更快
sudo make altinstall
```

> ⚠️ 建议用 `make altinstall`，避免覆盖系统默认的 `python3`。

---

### 5. 建立软链接

```bash
sudo ln -sf /usr/local/python3.13/bin/python3.13 /usr/local/bin/python3.13
sudo ln -sf /usr/local/python3.13/bin/pip3.13 /usr/local/bin/pip3.13
```

---

### 6. 环境变量设置

```bash
echo 'export LD_LIBRARY_PATH=/usr/local/python3.13/lib:$LD_LIBRARY_PATH' >> ~/.bashrc
echo 'export UV_LINK_MODE=copy' >> ~/.bashrc
source ~/.bashrc
```

---

✅ 完成后你可以检查版本：

```bash
python3.13 -V
pip3.13 -V
```

---

要不要我帮你顺手整理成一个 **一键安装的bash脚本**？
