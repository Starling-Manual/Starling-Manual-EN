# Building the Starling Manual

The _Starling Manual_ uses the [AsciiDoctor][1] toolchain to provide multiple output formats (HTML, PDF and EPUB) from a single, plain-text source written with the [AsciiDoc][2] markup language.

To build the manual yourself, you need will need to install AsciiDoctor itself and the [Pygments][3] library for syntax highlighting.
This means you will also have to install a few dependencies, like Ruby and Python.
This document will guide you through the installation process.

## Installation

### macOS and Linux

Apple's _macOS_ and most _Linux_ distributions have both Ruby and Python installed per default, which makes the process rather easy.

1. Install a couple of Ruby gems via:  
   `gem install rake bundler`
2. Install _pip_, the package manager for Python:  
   `sudo easy_install pip`
3. Use _pip_ to install _Pygments_:  
   `pip install pygments`
4. Install all required Ruby packages via:  
   `cd path/to/manual; bundle install`

### Windows

I recommend to use the package manager [Chocolatey][5] for easy installation of all dependencies.

1. Install _Chocolatey_.
2. Open an administrative command line (in Windows 10, right-clicking the Start button reveals such an option).
3. Install the basic packages via:  
   `choco install -y ruby python2 pip`
4. Use _pip_ to install _Pygments_:  
   `pip install pygments`
5. Install all required Ruby packages via:  
   `cd path/to/manual; bundle install`

## Compilation

The actual compilation is handled by [Rake][4].
To see all available Rake tasks, call:

    cd path/to/manual
    rake --tasks

If you simply call `rake`, the HTML version will be compiled to the `out` directory.
To compile PDF or EPUB versions, call:

    rake build_pdf
    rake build_epub

That's it!

[1]: http://asciidoctor.org
[2]: http://asciidoctor.org/docs/what-is-asciidoc
[3]: http://pygments.org
[4]: https://ruby.github.io/rake/
[5]: https://chocolatey.org
