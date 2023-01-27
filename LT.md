## Build boost python

    wget https://boostorg.jfrog.io/artifactory/main/release/1.81.0/source/boost_1_81_0.tar.gz
    tar zxvf boost_1_81_0.tar.gz && cd boost_1_81_0
    ./bootstrap.sh --with-python=/usr/local/python3.11/bin/python3.11
    ./b2 install --with-python include=/usr/local/python3.11/include
And set b2 and boost path.

## Build libtorrent python binding
    
...

## Fix libtorrent version

    cd /usr/local/python3.11/lib/python3.11/site-packages
    cd libtorrent-2.0.8-py3.11-linux-x86_64.egg/EGG-INFO
Change folder name, modify easy-install.pth and PKG_INFO.

## Fix Pycharm code insight

Move all from libtorrent folder to the parent folder.  
Change  '__init__' filename to 'libtorrent', change code in setup.py as well.  
Now auto-completion for libtorrent module is available in pycharm, but pycharm misunderstanding doc from boost.  
The first arg of function in a class is generated as the first arg of instance method(it's self).  
To fix this, clt+mouse to find the file then search and replace to remove redundant args.
    