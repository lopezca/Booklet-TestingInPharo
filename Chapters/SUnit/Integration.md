## Getting more with continuous integration
  #loading : [
    SCIMetacelloLoadSpec {
      #baseline : 'ContainersArray2D',
      #directory : 'src',
      #platforms : [ #pharo ]
    }
  ],
  #testing : {
    #coverage : {
      #packages : [ 'Containers-Array2D' ]
    }
  }
}

env:
  GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

on:
  push:
    branches:
      - master
  workflow_dispatch:
  
jobs:
  build:
    strategy:
      matrix:
        platform: [ubuntu-latest, macos-latest, windows-latest ]
    runs-on: ${{ matrix.platform }}
    steps:
      - uses: actions/checkout@v2
      - uses: hpi-swa/setup-smalltalkCI@v1
        id: smalltalkci
        with:
          smalltalk-version: Pharo64-8.0
      - run: smalltalkci -s ${{ steps.smalltalkci.outputs.smalltalk-version }}
        shell: bash
        timeout-minutes: 15

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  build:
    strategy:
      matrix:
        os: [ macos-latest, windows-latest ]
        smalltalk: [ Pharo64-8.0, Pharo64-7.0 ]
    runs-on: ${{ matrix.os }}
    name: ${{ matrix.smalltalk }} on ${{ matrix.os }}
    steps:
      - uses: actions/checkout@v2
      - name: Setup smalltalkCI
        uses: hpi-swa/setup-smalltalkCI@v1
        with:
          smalltalk-version: ${{ matrix.smalltalk }}
      - name: Load Image and Run Tests
        run: smalltalkci -s ${{ matrix.smalltalk }}
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        timeout-minutes: 15
sudo: false

# Select operating system(s)
os:
  - linux
  - osx

# Select compatible Smalltalk image(s)
smalltalk:

  - Pharo32-8.0
  - Pharo-7.0
  - Pharo-6.1

  - Pharo64-8.0
  - Pharo64-7.0
  CYG_ROOT: C:\cygwin
  CYG_BASH: C:\cygwin\bin\bash
  CYG_CACHE: C:\cygwin\var\cache\setup
  CYG_EXE: C:\cygwin\setup-x86.exe
  CYG_MIRROR: http://cygwin.mirror.constant.com
  SCI_RUN: /cygdrive/c/smalltalkCI-master/run.sh
  matrix:
    - SMALLTALK: Pharo-6.1
    - SMALLTALK: Pharo-7.0

platform:
  - x86

install:
  - '%CYG_EXE% -dgnqNO -R "%CYG_ROOT%" -s "%CYG_MIRROR%" -l "%CYG_CACHE%" -P unzip'
  - ps: Start-FileDownload "https://github.com/hpi-swa/smalltalkCI/archive/master.zip" "C:\smalltalkCI.zip"
  - 7z x C:\smalltalkCI.zip -oC:\ -y > NULL

build: false

test_script:
  - '%CYG_BASH% -lc "cd $APPVEYOR_BUILD_FOLDER; exec 0</dev/null; $SCI_RUN"'