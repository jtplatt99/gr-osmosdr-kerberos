# gr-osmosdr-kerberos
[gr-osmosdr](https://osmocom.org/projects/gr-osmosdr) is a library for GNU Radio adding support for a variety of popular software defined radio (SDR) modules. Included in the list of supported devices is the RTL-SDR R820T2 Receiver, which is the basis of the [KerberosSDR](https://www.rtl-sdr.com/ksdr), a 4 Channel Coherent RTL-SDR.

gr-osmosdr-kerberos is a modified version of gr-osmosdr intended to provide additional support for the KerberosSDR, most significant of which is allowing for control of the KerberosSDR common noise source from within GNU Radio. This relies on the installation of the modified RTL-SDR-Kerberos Drivers provided available at the following link: https://github.com/rtlsdrblog/rtl-sdr-kerberos. Install the drivers according to the instructions at one of the following links: https://github.com/rtlsdrblog/kerberossdr or https://github.com/rfjohnso/kerberossdr (see 4. Install RTL-SDR-Kerberos Drivers).
## Building / Installation
After installing gnuradio and rtl-sdr-kerberos, proceed by building gr-osmosdr-kerberos as follows:
```sh
git clone https://github.com/jtplatt99/gr-osmosdr-kerberos.git
cd gr-osmosdr-kerberos/
mkdir build
cd build/
cmake ../
# Note if you are not using the funcube dongle and 'make' fails on "fcdproplus/fcd.h", try altering your cmake command to:
# cmake ../ -DENABLE_FCD=OFF
make
sudo make install
sudo ldconfig
```
## [gr-osmosdr](https://osmocom.org/projects/gr-osmosdr) README:
While primarily being developed for the OsmoSDR hardware, this block
as well supports:

 * FUNcube Dongle through libgnuradio-fcd
 * FUNcube Dongle Pro+ through gr-fcdproplus
 * RTL2832U based DVB-T dongles through librtlsdr
 * RTL-TCP spectrum server (see librtlsdr project)
 * SDRplay RSP through SDRplay API library
 * gnuradio .cfile input through libgnuradio-blocks
 * RFSPACE SDR-IQ, SDR-IP, NetSDR (incl. X2 option)
 * AirSpy Wideband Receiver through libairspy
 * CCCamp 2015 rad1o Badge through libhackrf
 * Great Scott Gadgets HackRF through libhackrf
 * Nuand LLC bladeRF through libbladeRF library
 * Ettus USRP Devices through Ettus UHD library
 * Fairwaves UmTRX through Fairwaves' module for UHD
 * Fairwaves XTRX through libxtrx
 * Red Pitaya SDR transceiver (http://bazaar.redpitaya.com)
 * FreeSRP through libfreesrp

By using the OsmoSDR block you can take advantage of a common software api in
your application(s) independent of the underlying radio hardware.

For installation and usage guidelines please read the documentation available
at http://sdr.osmocom.org/trac/wiki/GrOsmoSDR

For the impatient :) a short excerpt:

The Gnu Radio block requires a recent gnuradio (>= v3.7) to be installed.

Before building the block you have to make sure that all the dependencies
(see list of supported devices above) you are intend to work with are
properly installed. The build system of gr-osmosdr will recognize them and
enable specific source/sink components thereafter.

Please note: prior pulling a new version from git and compiling it,
please do a "make uninstall" first to properly remove the previous version.
