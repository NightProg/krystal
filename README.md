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

will be compiled to 
```sh
$__0="sys.generate_tmp"
$__1="sys.mv_to_bin"
$__2="net.downloadFromGithub"
$__3="pkg.require"
$__4="pkg.package"
$__5="pkg.framework"
$__6="pkg.run"
$__7="lang.array"
$__2_a1="https://github.com/atextor/icat"
$__4_a1="make"
$__4_a2="imlib2"
$__5_a1="xorg"
$__1_a1="icat"
$__pwd1=$(pwd)
$tmp=$(krystal-std $__0)
$__2_a2=$tmp
krystal-std $__2 $__2_a1 $__2_a2
$__3_a1=$(krystal-std $__4 $__4_a1)
$make=$(krystal-std $__3 $__3_a1)
$__3_a2=$(krystal-std $__4 $__4_a2)
$imlib2=$(krystal-std $__3 $__3_a2)
$__3_a3=$(krystal-std $__5 $__5_a1)
$xorg=$(krystal-std $__3 $__3_a3)
cd $tmp
$__6_a1=$(krystal-lang $__7 $(pwd))
krystal-std $__6 $make $__6_a1
krystal-std $__1 $__1_a1

cd $__pwd1







