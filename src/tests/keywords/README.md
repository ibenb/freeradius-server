# The Keyword test Framework

See "update" and "default-input.attrs" for examples.

In short, the test framework assumes Access-Request with PAP
authentication.  The password is hard-coded into the configuration,
and can't be changed.

The entire test suite consists of two files:

* FOO

  Contains a short piece of "unlang".  The shorter the better.  The
  goal is to do something useful in unlang, and modify the input
  packet and/or the reply.

  If the test depends on another one, it should name the other test
  at the top of the file.  For example, the `if-else` test depends
  on the `if` test.  This dependency is given by the following lines
  at the top of the `if-else` file:

  `# PRE: if`

* FOO.attrs

  Contains the input packet and the filter for the reply.  There
  always has to be attributes in the input, and filter attributes in the
  reply.

  If FOO.txt doesn't exist, then the "default-input.attrs" file is used.
  This allows many tests to be simplified, as all they need is a little
  bit of "unlang".

## How it works.

The input packet is passed into the unit test framework, through the
FOO unlang snippet, and filtered through the reply filter.  If
everything matches, then the test case passes.