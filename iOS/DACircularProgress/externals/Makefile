
POD=pod
XCODEBUILD=/Applications/Xcode.app/Contents/Developer/usr/bin/xcodebuild

TARGET=Pods
LIB_NAME=DACircularProgress
LIB_OUTPUT=lib$(LIB_NAME).a
PROJ=Pods/Pods.xcodeproj

all: lib$(LIB_NAME).a

Podfile.lock :
	$(POD) --no-integrate install

lib$(LIB_NAME)-i386.a: Podfile.lock
	$(XCODEBUILD) -project $(PROJ) -target $(TARGET) -sdk iphonesimulator -arch i386 -configuration Release clean build	
	mv build/Release-iphonesimulator/$(LIB_OUTPUT) $@

lib$(LIB_NAME)-x86_64.a: Podfile.lock
	$(XCODEBUILD) -project $(PROJ) -target $(TARGET) -sdk iphonesimulator -arch x86_64 -configuration Release clean build
	mv build/Release-iphonesimulator/$(LIB_OUTPUT) $@

lib$(LIB_NAME)-armv7.a: Podfile.lock
	$(XCODEBUILD) -project $(PROJ) -target $(TARGET) -sdk iphoneos -arch armv7 -configuration Release clean build
	mv build/Release-iphoneos/$(LIB_OUTPUT) $@

lib$(LIB_NAME)-armv7s.a: Podfile.lock
	$(XCODEBUILD) -project $(PROJ) -target $(TARGET) -sdk iphoneos -arch armv7s -configuration Release clean build
	mv build/Release-iphoneos/$(LIB_OUTPUT) $@

lib$(LIB_NAME)-arm64.a: Podfile.lock
	$(XCODEBUILD) -project $(PROJ) -target $(TARGET) -sdk iphoneos -arch arm64 -configuration Release clean build
	mv build/Release-iphoneos/$(LIB_OUTPUT) $@

lib$(LIB_NAME).a: lib$(LIB_NAME)-i386.a lib$(LIB_NAME)-x86_64.a lib$(LIB_NAME)-armv7.a lib$(LIB_NAME)-armv7s.a lib$(LIB_NAME)-arm64.a 
	lipo -create -output $@ $^

clean:
	rm -rf Podfile.lock Pods *.a build/

.PHONY: all clean

