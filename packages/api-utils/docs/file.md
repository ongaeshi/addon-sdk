<!-- contributed by Drew Willcoxon [adw@mozilla.com]  -->
<!-- contributed by Atul Varma [atul@mozilla.com]  -->
<!-- edited by Noelle Murata [fiveinchpixie@gmail.com]  -->


The `file` module provides access to the local filesystem.

<api name="basename">
@function
  Returns the last component of the given path.  For example,
  `basename("/foo/bar/baz")` returns `"baz"`.  If the path has no components,
  the empty string is returned.
@param path {string}
  The path of a file.
@returns {string}
  The last component of the given path.
</api>

<api name="dirname">
@function
  Returns the path of the directory containing the given file.  If the file is
  at the top of the volume, the empty string is returned.
@param path {string}
  The path of a file.
@returns {string}
  The path of the directory containing the file.
</api>

<api name="exists">
@function
  Returns true if a file exists at the given path and false otherwise.
@param path {string}
  The path of a file.
@returns {boolean}
  True if the file exists and false otherwise.
</api>

<api name="join">
@function
  Takes a variable number of strings, joins them on the file system's path
  separator, and returns the result.
@param ... {strings}
  A variable number of strings to join.
@returns {string}
  A single string formed by joining the strings on the file system's path
  separator.
</api>

<api name="list">
@function
  Returns an array of file names in the given directory.
@param path {string}
  The path of the directory.
@returns {array}
  An array of file names.  Each is a basename, not a full path.
</api>

<api name="mkpath">
@function
  Makes a new directory named by the given path.  Any subdirectories that do not
  exist are also created.  `mkpath` can be called multiple times on the same
  path.
@param path {string}
  The path to create.
</api>

<api name="open">
@function
  Returns a stream providing access to the contents of a file.
@param path {string}
  The path of the file to open.
@param [mode] {string}
  An optional string, each character of which describes a characteristic of the
  returned stream.  If the string contains `"r"`, the file is opened in
  read-only mode.  `"w"` opens the file in write-only mode.  `"b"` opens the
  file in binary mode.  If `"b"` is not present, the file is opened in text
  mode, and its contents are assumed to be UTF-8.  If *`mode`* is not given,
  `"r"` is assumed, and the file is opened in read-only text mode.
@returns {stream}
  If the file is opened in text read-only `mode`, a `TextReader` is returned,
  and if text write-only mode, a `TextWriter` is returned.  See
  [`text-streams`](packages/api-utils/docs/text-streams.html) for information on
  these text stream objects.  If the file is opened in binary read-only `mode`,
  a `ByteReader` is returned, and if binary write-only mode, a `ByteWriter` is
  returned.  See
  [`byte-streams`](packages/api-utils/docs/byte-streams.html) for more
  information on these byte stream objects.  Opened files should always be
  closed after use by calling `close` on the returned stream.
</api>

<api name="read">
@function
  Opens a file and returns a string containing its entire contents.
@param path {string}
  The path of the file to read.
@param [mode] {string}
  An optional string, each character of which describes a characteristic of the
  returned stream.  If the string contains `"b"`, the contents will be returned 
  in binary mode. If `"b"` is not present or `mode` is not given, the file
  contents will be returned in text mode. 
@returns {string}
  A string containing the file's entire contents.
</api>

<api name="remove">
@function
  Removes a file from the file system.  To remove directories, use `rmdir`.
@param path {string}
  The path of the file to remove.
</api>

<api name="rmdir">
@function
  Removes a directory from the file system.  If the directory is not empty, an
  exception is thrown.
@param path {string}
  The path of the directory to remove.
</api>
