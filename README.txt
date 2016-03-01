==============UHD Installation===================
sudo apt-get install libboost-all-dev libusb-1.0-0-dev python-mako doxygen python-docutils cmake build-essential
sudo apt-get install liborc-0.4-dev python-cheetah
tar -xzvf $UHD_SRC_NAME
cd UHD/
mkdir build
cd build/
cmake ../
sudo make
*sudo make test
sudo make install
sudo ldconfig

===============GNURadio Installation===============
sudo apt-get install git libtool swig libfftw3-dev libcppunit-dev libgsl0-dev sdcc libsdl1.2-dev python-wxgtk2.8 python-numpy python-qt4 python-qwt5-qt4 libxi-dev libqwt5-qt4-dev libfontconfig1-dev libxrender-dev libzmq-dev python-sphinx libcomedi-dev libjack-dev
tar -xzvf $GR_SRC_NAME
cd GR/
mkdir build
cd build/
cmake ../
sudo make
*sudo make test
sudo make install
sudo ldconfig
gedit .bashrc
|_ export PYTHONPATH=$PYTHONPATH:/usr/lib/python2.7:/usr/local/lib/python2.7/dist-packages:/usr/local/lib/python2.7/site-packages:/usr/local/share/gnuradio
|_ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/python2.7:/usr/local/share/gnuradio:/usr/lib:/usr/local/lib


==============GNURadio OFDM====================
sudo apt-get install libitpp-dev liblog4cpp5-dev python-opengl
git clone https://github.com/bastibl/gr-foo.git
cd gr-foo
mkdir build
cd build
cmake ..
make
sudo make install
sudo ldconfig
git clone git://github.com/bastibl/gr-ieee802-11.git
cd gr-ieee802-11
mkdir build
cd build
cmake ..
make
sudo make install
sudo ldconfig

==============GNURadio Broadcast====================
cd gr-ieeebroadcast
mkdir build
cd build
cmake ..
make
sudo make install
sudo ldconfig

==============Before Experiments====================
sudo sysctl -w kernel.shmmax=2147483648
volk_profile


NOTICE
- a known bad version of Boost(v104601)
	(cmake ../ -DENABLE_BAD_BOOST=ON
- apt-cache search gnu radio
	(-- if you want to enable more components in gnuradio package)
- autoreconf -fiv
	(-- dealing with libtool mismatch)
- sudo apt-get -y install libxrender-dev libxrender1 libxrender1-dbg
	(-- dealing with -lXrender missing)
- sudo apt-get -y install fontconfig fontconfig-config libfontconfig1 libfontconfig1-dbg libfontconfig1-dev
	(-- dealing with -lfontconfig missing)
- copy corresponding .pc files to /usr/local/lib/pkgconfig
	(-- dealing with wicom.pc not found)

