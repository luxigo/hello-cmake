## Build and install debug version in /usr/local with
    mkdir build
    cd build
    cmake ..
    sudo make all install

## Build and install release verison in /usr with
    mkdir build
    cd build
    cmake .. -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr
    sudo make all install

## Install in some other directory using DESTDIR, eg:
    make all install DESTDIR=$(pwd)/dist


