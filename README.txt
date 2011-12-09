twolame with all the required changed via install_name_tool to @executable_path/../Resources/$libname

I used an alternate install location for macports with a long name so there would be space to change the path.

Here are the calls:

# libFLAC.8.dylib
install_name_tool -id @executable_path/../Resources/libFLAC.8.dylib  libFLAC.8.dylib
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libogg.0.dylib @executable_path/../Resources/libogg.0.dylib  libFLAC.8.dylib

# libogg.0.dylib
install_name_tool -id @executable_path/../Resources/libogg.0.dylib libogg.0.dylib

# libsndfile.1.dylib
install_name_tool -id @executable_path/../Resources/libsndfile.1.dylib libsndfile.1.dylib
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libFLAC.8.dylib @executable_path/../Resources/libFLAC.8.dylib libsndfile.1.dylib
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libvorbisenc.2.dylib @executable_path/../Resources/libvorbisenc.2.dylib libsndfile.1.dylib
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libvorbis.0.dylib @executable_path/../Resources/libvorbis.0.dylib libsndfile.1.dylib
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libogg.0.dylib @executable_path/../Resources/libogg.0.dylib libsndfile.1.dylib

# libtwolame.0.dylib
install_name_tool -id @executable_path/../Resources/libtwolame.0.dylib libtwolame.0.dylib

# libvorbis.0.dylib
install_name_tool -id @executable_path/../Resources/libvorbis.0.dylib libvorbis.0.dylib
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libogg.0.dylib @executable_path/../Resources/libogg.0.dylib libvorbis.0.dylib

# libvorbisenc.2.dylib
install_name_tool -id @executable_path/../Resources/libvorbisenc.2.dylib libvorbisenc.2.dylib
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libvorbis.0.dylib @executable_path/../Resources/libvorbis.0.dylib libvorbisenc.2.dylib
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libogg.0.dylib @executable_path/../Resources/libogg.0.dylib libvorbisenc.2.dylib

# twolame
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libsndfile.1.dylib @executable_path/../Resources/libsndfile.1.dylib twolame 
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libFLAC.8.dylib @executable_path/../Resources/libFLAC.8.dylib  twolame
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libvorbisenc.2.dylib @executable_path/../Resources/libvorbisenc.2.dylib  twolame
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libvorbis.0.dylib @executable_path/../Resources/libvorbis.0.dylib  twolame
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libogg.0.dylib @executable_path/../Resources/libogg.0.dylib  twolame
install_name_tool -change /macports-alternate-install-location-longname/local/lib/libtwolame.0.dylib @executable_path/../Resources/libtwolame.0.dylib twolame