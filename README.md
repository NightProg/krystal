# krystal
A Modern Compiler Shell Langage Made In Rust

# Example

in Krystal
```sh
import std.sys.generate_tmp;
import std.sys.mv_to_bin;
import std.net.downloadFromGithub;
import std.pkg.require;
import std.pkg.package;
import std.pkg.framework;
import std.pkg.run;

$tmp = generate_tmp;

downloadFromGithub "https://github.com/atextor/icat", $tmp;

$make = require (package "make");
$imlib2 = require (package "imlib2");
$xorg = require (framework "xorg");

in $tmp do {
  run $make, [$PWD];
  mv_to_bin icat;
}
```

will be compiled to (**CMD**: ```krystalc icat.kr --with-std --lang sh```)
```sh
__0="sys.generate_tmp"
__1="sys.mv_to_bin"
__2="net.downloadFromGithub"
__3="pkg.require"
__4="pkg.package"
__5="pkg.framework"
__6="pkg.run"
__7="lang.array"
__2_a1="https://github.com/atextor/icat"
__4_a1="make"
__4_a2="imlib2"
__5_a1="xorg"
__1_a1="icat"
__pwd1=$(pwd)
tmp=$(krystal-std $__0)
__2_a2=$tmp
krystal-std $__2 $__2_a1 $__2_a2
__3_a1=$(krystal-std $__4 $__4_a1)
make=$(krystal-std $__3 $__3_a1)
__3_a2=$(krystal-std $__4 $__4_a2)
imlib2=$(krystal-std $__3 $__3_a2)
__3_a3=$(krystal-std $__5 $__5_a1)
xorg=$(krystal-std $__3 $__3_a3)
cd $tmp
__6_a1=$(krystal-lang $__7 $(pwd))
krystal-std $__6 $make $__6_a1
krystal-std $__1 $__1_a1

cd $__pwd1
```

## Usage of no_std

if your system doesn't have the Krystal STD you can use the option `--no-std`:

`krystalc icat.kr --no-std --lang sh`
this will generate a biggest script file
```sh
__0="make"
__1="imlib2"
__2="xorg"
__3="icat"
__4="https://github.com/atextor/icat"
__PWD1=$(pwd)
__TRUE=1
__FALSE=0
__CFG_NO_STD=__TRUE
__CFG_PKG_MANAGER_EXIST=__TRUE
__CFG_PKG_MANAGER="brew"
__CFG_PKG_MANAGER_INSTALL_CMD="install"
__CFG_OS="macos" # note: krystalc generate a target file for your os if you wanna generate a cross platform script use `--all-target` option
__CFG_MSG_ERR_NO_PKG_MANAGER="There isn't package manager in this os"
__CFG_EXIT_CODE_ERR_NO_PKG_MANAGER=2
__CFG_GIT_TOOL="git"
__CFG_NET_TOOL="curl"
__CFG_API_HUB="https://hub.krystal.dev/"
__CFG_TMP_PATH="/tmp"
__CFG_BIN_PATH="/local/bin"
__krystal__exist() {
    if which $0 >/dev/null; then
        return $__TRUE
    else
        return $__FALSE
    fi
}

__krystal__error() {
    echo "Error when running $0: $1"
    exit $2
}

__krystal__install() {
  if [ $__CFG_PKG_MANAGER_EXIST -eq $__TRUE ]; then
      $__CFG_PKG_MANAGER $__CFG_PKG_MANAGER_INSTALL_CMD $0
  else
      __krystal__error "__krystal__install" $__CFG_MSG_ERR_NO_PKG_MANAGER $__CFG_EXIT_CODE_ERR_NO_PKG_MANAGER
  fi
}

__krystal_generatetmp() {
    __0_0="$__CFG_TMP_PATH/$RANDOM"
    mkdir $__0_0
    echo $__0_0
}   
    
      
__krystal_downloadFromGithub() {
    __krystal__exist $__CFG_GIT_TOOL
    if [ $? -eq $__FALSE ]; then
        __krystal__install $__CFG_GIT_TOOL
    else
        $__CFG_GIT_TOOL clone $0 $1
    fi
}

_krystal_package() {
    __krystal__exist  $__CFG_NET_TOOL
    if [ $? -eq $__FALSE ]; then
        __krystal__install $__CFG_NET_TOOL
    else
        echo "$($__CFG_NET_TOOL "$__CFG_API_HUB/package/$0")"
    fi
}

_krystal_framework() {
    __krystal__exist  $__CFG_NET_TOOL
    if [ $? -eq $__FALSE ]; then
        __krystal__install $__CFG_NET_TOOL
    else
        echo "$($__CFG_NET_TOOL $__CFG_API_HUB/framework/$0)"
    fi
}

_krystal_require() {
    __krystal__exist  $__CFG_NET_TOOL
    if [ $? -eq $__FALSE ]; then
        __krystal__install $__CFG_NET_TOOL
    else
        __0_0="$($__CFG_NET_TOOL $__CFG_API_HUB/api/name/$0)"
        __krystal__exist $__0_0
        if [ $? -eq $__FALSE ]; then
            __krystal__install  $__0_0
        fi
        echo "$__0_0"            
    fi
}

_krystal_run() {
    $0 $1
}

_krystal_mv_to_bin() {
  mv $0 $__CFG_BIN_PATH
}

tmp="$(__krystal_generatetmp)"


_krystal_downloadFromGithub $__4 $tmp
__1_0=$(_krystal_package $__0)
make=$(_krystal_require __1_0)
__1_1=$(_krystal_package $__1)
imlib2=$(_krystal_require $__1_1)
__1_2=$(_krystal_framework $__2)
xorg=$(_krystal_require $__1_2)

cd $tmp
_krystal_run $make $(pwd)
_krystal_mv_to_bin icat
cd $__PWD1



