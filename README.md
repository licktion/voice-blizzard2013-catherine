# voice-blizzard2013-catherine

You need to have `blizzard2013-data` *beside* your `voice-blizzard2013-catherine` clone.
That data directory should be obtained from `coli:/proj/marytts.shadow/blizzard2013/blizzard2013-data`, where `coli` is an alias for your access to `login.coli.uni-saarland.de`.
The file `BlackBeauty.zip` must exist in the data directory.

## Prerequisites

`praat`, `sox`, `ch_track`, and `wagon` must be on the `PATH`.
If this is not the case, install Praat, Sox, and the Edinburgh Speech Tools

### OSX with Homebrew and Cask:
```
$ brew cask install praat sox
$ brew install speech-tools
```

### Linux (Debian, Ubuntu, etc.):
```
$ sudo apt-get install praat sox speech-tools
```

The Gradle voicebuilding plugin is resolved from the `buildSrc`, which is a Git submodule.
Therefore, ensure that it has been initialized, and is up-to-date.
Otherwise, run
```
$ git submodule update --init
```

## Building the voice

First, prepare the raw data:
```
$ ./gradlew prepareVoicebuilding
```

Then, initialize the legacy voicebuilding project layout:
```
$ ./gradlew legacyInit
```

Finally, assemble the voice package:
```
$ ./gradlew assemble
```
The files will be created under `build/distributions` and can be dropped into the `download` directory of a MaryTTS instance for installation.

Alternatively, the voice can be built and run directly in an ad-hoc MaryTTS server:
```
$ ./gradlew run
```
When ready, navigate to http://localhost:59125/ in your web browser.
