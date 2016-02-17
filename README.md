# coreaudio-sys [![Build Status](https://travis-ci.org/RustAudio/coreaudio-sys.svg?branch=master)](https://travis-ci.org/RustAudio/coreaudio-sys) [![Crates.io](https://img.shields.io/crates/v/coreaudio-sys.svg)](https://crates.io/crates/coreaudio-sys) [![Crates.io](https://img.shields.io/crates/l/coreaudio-sys.svg)](https://github.com/RustAudio/coreaudio-sys/blob/master/LICENSE)

Raw bindings to Apple's Core Audio API for OS X and iOS generated using [rust-bindgen](https://github.com/crabtw/rust-bindgen) for use with [coreaudio-rs](https://github.com/RustAudio/coreaudio-rs).

Bindings generated as follows:

    # to use rust-bindgen to generate bindings on OSX:
    export DYLD_LIBRARY_PATH=/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/lib/

	echo '#include <AudioUnit/AudioUnit.h>' > src/CoreAudioInclude.h
	echo '#include <AudioToolbox/AudioToolbox.h>' >> src/CoreAudioInclude.h
	clang -E src/CoreAudioInclude.h > src/CoreAudio.h
	rust-bindgen/target/release/bindgen -framework-link AudioUnit -framework-link AudioToolbox -framework-link CoreServices -o src/core_audio.rs -builtins src/CoreAudio.h
