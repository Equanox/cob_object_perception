all: installed

TARBALL = build/zxing-2.1.tar.gz
TARBALL_URL = https://code.ros.org/svn/release/download/thirdparty/zxing-2.1.tar.gz # originally from http://zxing.googlecode.com/files/ZXing-2.1.zip
SOURCE_DIR = build/zxing-2.1
MD5SUM_FILE = zxing-2.1.tar.gz.md5sum

include $(shell rospack find mk)/download_unpack_build.mk

installed: $(SOURCE_DIR)/unpacked
	cd $(SOURCE_DIR)/core && ant &&  cd ../javase && ant && cd ../cpp && scons lib 
	
	# copy to common
	mkdir -p common
	mkdir -p common/lib
	mkdir -p common/include
	#&& ln -s `pwd`/core/src ../../../include &&
	cp $(SOURCE_DIR)/cpp/build/libzxing.a common/lib
	cp -r $(SOURCE_DIR)/cpp/build/core/src/* common/include
	#mkdir tmp
	#cd $(SOURCE_DIR)/cpp/build/core/src && find -name '*.h'
	cd common/include && rm `find -type f -not -name '*.h'`

clean:
	rm -rf common $(SOURCE_DIR) $(TARBALL)

wipe: clean
	-rm -rf build
