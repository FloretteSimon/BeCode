Not the must fun part of the install because I had issues with the make command but I figure it out and here we go:


## 1. Download zip file:

https://zeek.org/get-zeek/


## 2. Ensure All Dependencies Are Installed:

sudo apt-get install cmake make gcc g++ flex bison libpcap-dev libssl-dev python3 python3-dev zlib1g-dev


## 3. Unzip:

cd /home/kali/Download/

tar -xzf zee-7.0.0.tar.gz

cd zeek-7.0.0


## 4. Downloading the source code as a Git repository to ensure all necessary components are included:

git clone https://github.com/zeek/zeek.git

cd zeek

git checkout v7.0.0  # Checkout the specific version you need

git submodule update --init --recursive


## 5. Proceed with the build:

mkdir -p build

cd build

cmake ..

make ##take time

sudo make install
