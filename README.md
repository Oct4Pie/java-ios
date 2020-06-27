# java-ios
Compile native executables for iOS using GraalVM's native-image

# Setup
You need to have brew installed: https://brew.sh
* Download `graalvm-ce-java11-darwin-amd64-20.2.0-dev.tar.gz`, the developer version of graalvm's SDK, from https://github.com/graalvm/graalvm-ce-dev-builds/releases
 >`tar -C /usr/local/opt/ -xvf /path/to/graalvm-ce-java11-darwin-amd64-20.2.0-dev.tar.gz`

* Install libimobiledevice, native iOS libraries: <br />
   >`brew install --HEAD libimobiledevice`

# Compiling the sample
* `export GRAALVM_HOME=/usr/local/opt/graalvm-ce-java11-20.2.0-dev/Contents/Home`
* `export JAVA_HOME=$GRAALVM_HOME`
* `git clone https://github.com/m3hdi652/java-ios.git && cd java-ios/HelloJava`
* Using Maven:<br />
    >`mvn client:build`
* If the compilation is successful, the `HelloJava` will appear in **dist** folder
* You can fake-sign the binary by using ldid: <br />
    >`brew install ldid` <br />
    >`ldid -S HelloJava`

* You also can codesign the binary, if you have a free or paid developer account: <br />
    > Get your identity by `security find-identity -p codesigning -v`<br />
    > e.g: <br />

    >>1) 2CD708151B6469F3D4B0F05F48338B81F1809C82 "Apple Development: example@example.com (5J8I29WF1D)" <br />
        >> 1 valid identities found <br />
    
    >>`codesign -fs "Apple Development: example@example.com (5J8I29WF1D)" /path/to/binary`

# Credits/Sources
https://github.com/graalvm/graalvm-ce-dev-builds <br />
https://github.com/gluonhq <br />
https://github.com/gluonhq/client-samples <br />
https://github.com/gluonhq/substrate <br />
