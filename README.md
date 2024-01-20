# krystal
A Modern Compiler Shell Langage Made In Rust

# Example

in Krystal
```sh
import std.tmp.generate_tmp;
import std.sys.mv_to_bin;
import std.net.downloadFromGithub;
import std.pkg.require;
import std.pkg.package;
import std.pkg.framework;
import std.pkg.run;

$tmp = generate_tmp;

(downloadFromGithub "https://github.com/atextor/icat", $tmp);

$make = (require (package "make"));
$imlib2 = (require (package "imlib2"));
$xorg = (require (framework "xorg"));

in $tmp do {
  (run $make, [$PWD]);
  (mv_to_bin icat);
}
```
