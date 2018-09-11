# ads
[![Build Status](https://travis-ci.com/acwilson96/ads.svg?branch=master)](https://travis-ci.com/acwilson96/ads)
![License](https://img.shields.io/badge/License-MIT-brightgreen.svg)


Advanced Data Structures - Data Structures not provided in C++ STL Library.

# Download
```
git clone https://github.com/acwilson96/ads
cd Trie
```
The following should be run from within the "ads" directory.
# Release Install
Install all libraries provided in ads.
```
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
make
make install
cd ..
```
# Debug Install & Run Unit Tests
```
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Debug ..
make
make install
ctest -V
cd ..
```
# Uninstall
```
cd build
xargs rm < install_manifest.txt
cd ..
rm -rf ./build/
```
