# Verifiable-Audits-for-IRVElections
## Install gmp

Download the latest version of gmp from https://gmplib.org/ or run the following command for version 6.3.0:
```
wget https://gmplib.org/download/gmp/gmp-6.3.0.tar.xz
tar -xf gmp-6.3.0.tar.xz
cd gmp-6.3.0/
./configure
make
```
Some self-tests can be run with
```
make check
```
And you can install (under /usr/local by default) with
```
sudo make install
cd ..
```
## Install mpfr

download latest version of mpfr from https://www.mpfr.org/mpfr-current/#download or run the following command for version 4.2.1:
```
wget https://www.mpfr.org/mpfr-current/mpfr-4.2.1.tar.xz
tar -xf mpfr-4.2.1.tar.xz
cd mpfr-4.2.1/
./configure
make
make check
sudo make install
cd ..
```
## Install FLINT 2.9 (It must be version 2.9)
```
git clone -b flint-2.9 --single-branch https://github.com/flintlib/flint.git
cd flint
./configure --disable-static
make -j N
```
where N is the number of jobs number allowed to run parallel. Typically, the fastest way to build is to let N be the number of threads your CPU plus one, which can be obtained in Bash through 
```
echo $(expr $(nproc) + 1)
```

We also recommend that you check that the library works as it should through make check, or make -j N check for a parallel check, before installing.
```
sudo make install
cd ..
```
## Other dependencies
```
sudo apt-get install libgmp-dev
sudo apt-get install libmpc-dev
```
## Mixnet
```
git clone https://github.com/dfaranha/lattice-verifiable-mixnet.git
cd lattice-verifiable-mixnet
mkdir deps
cd deps
cmake ../NFLlib -DCMAKE_BUILD_TYPE=Release -DNFL_OPTIMIZED=ON
make
make test
cd ..
make all
./bgv
./shuffle
```
