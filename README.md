# reeborg-docs
Documentation (Python tutorial and how to use Reeborg)
in multiple languages for http://reeborg.ca/docs/en, etc.

## To make a new language version

The simplest way to create a new language version is to start from an
existing one (say the "en" version) and translate the .rst files
one at a time.

Note that you may need to install
https://pypi.python.org/pypi/sphinxcontrib-inlinesyntaxhighlight

You may get an error about not being able to import module reeborg_xx
in help.rst. You can just ignore such error.

### Editing the relevant make file

You will need to edit the make.bat or the Makefile (depending on your
operating system) to replace "en" by the two-letter code of your language
for the following five lines in make.bat:

- set ALLSPHINXOPTS=-d %BUILDDIR%/doctrees_en %SPHINXOPTS%

- rd /s /q en

- rd /s /q doctrees_en

- %SPHINXBUILD% -b html %ALLSPHINXOPTS% %BUILDDIR%/en

- echo.Build finished. The HTML pages are in
%BUILDDIR%/en.

or (and this is untested) the following ones in Makefile:

- ALLSPHINXOPTS   = -d $(BUILDDIR)/doctrees_en $(PAPEROPT_$(PAPER)) $(SPHINXOPTS) .

- $(SPHINXBUILD) -b html $(ALLSPHINXOPTS) $(BUILDDIR)/en

- @echo "Build finished. The HTML pages are in $(BUILDDIR)/en."

Note that, in both cases, `BUILDDIR=../../_build` instead of `BUILDDIR=_build`


### Editing the relevant conf.py file

to do

### Editing the relevant theme files

to do

### Optional: create new images

to do
