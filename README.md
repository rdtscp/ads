# ads
<<<<<<< HEAD

[![Build Status](https://travis-ci.com/acwilson96/ads.svg?branch=master)](https://travis-ci.com/acwilson96/ads)
=======
[![Build Status](https://travis-ci.com/rdtscp/ads.svg?branch=master)](https://travis-ci.com/rdtscp/ads)
>>>>>>> 0455a17c679271022928ad85078aca918bd78896
![License](https://img.shields.io/badge/License-MIT-brightgreen.svg)

Advanced Data Structures - Data Structures not provided in C++ STL Library.

-   [Trie](https://github.com/acwilson96/trie)
-   [Binary Tree](https://github.com/acwilson96/bin_tree)
-   [Bloom Filter](https://github.com/acwilson96/bloom_filter)

# Download

    git clone https://github.com/acwilson96/ads
    cd ads

# Usage

-   [trie.h](https://github.com/acwilson96/trie/blob/master/include/trie.h)
-   [bin_tree.h](https://github.com/acwilson96/bin_tree/blob/master/include/bin_tree.h)
-   [bloom_filter.h](https://github.com/acwilson96/bloom_filter/blob/master/include/bloom_filter.h)
    # Release Install
    Install all libraries provided in ads.


    mkdir build
    cd build
    cmake -DCMAKE_BUILD_TYPE=Release ..
    make
    make install
    cd ..

# Debug Install & Run Unit Tests

    mkdir build
    cd build
    cmake -DCMAKE_BUILD_TYPE=Debug ..
    make
    make install
    ctest -V
    cd ..

# Uninstall

    cd build
    xargs rm < install_manifest.txt
    cd ..
    rm -rf ./build/
