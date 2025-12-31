# Building the Starling Manual

The _Starling Manual_ uses the [Asciidoctor][1] toolchain to generate multiple output formats (HTML and PDF) from a single source written in the [AsciiDoc][2] markup language.

All required Ruby dependencies are managed via Bundler. Source code highlighting is handled by Asciidoctor’s built-in support for the Rouge highlighter, so no external syntax-highlighting tools are required.

## Installation

To build the manual, you need a working Ruby installation (version 2.7 or newer recommended).

1. Install Ruby if it’s not already available on your system.
2. Install Bundler (if necessary):
   `gem install bundler`
3. Install all required dependencies:
   `bundle install`

## Compilation

The actual compilation is handled by [Rake][4], which is included via the project’s Ruby dependencies.
To see all available Rake tasks, call:

    cd path/to/manual
    rake --tasks

If you simply call `rake`, the HTML version will be compiled to the `out` directory.
To compile the PDF version, call:

    rake build_pdf

That's it!

[1]: http://asciidoctor.org
[2]: http://asciidoctor.org/docs/what-is-asciidoc
[4]: https://ruby.github.io/rake/
[5]: https://chocolatey.org
