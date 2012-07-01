_ = require \slake-build-utils
fs = _.fs

global <<< require \prelude-ls
defer = process.next-tick

# == Configuration =====================================================
defaults = void
environment =
  package: require './package.json'

# == Tasks =============================================================
task \clean 'Removes all build artifacts.' ->
  defer _.display-errors
  _.header "› Removing all build artifacts..."
  each fs.remove, <[ lib build dist test/build ]>


task \build 'Builds JavaScript files out of LiveScript ones.' ->
  defer _.display-errors
  _.tasks.compile-ls \src \lib compile:defaults, environment:environment


task \package 'Packages stuff in a nice .tar.gz package.' ->
  version = environment.package.version
  libname = environment.package.name
  fs.initialise \dist
  fs.copy \build "dist/#libname-#version"
  _.tasks.pack \dist "#libname-#version" ["#libname-#version"] _.display-errors
