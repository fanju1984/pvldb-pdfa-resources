# How to ensure PDF/A compliance

This is a collection of resources started as part of the PVLDB Vol 17 Publication Process. It outlines various resources and how-tos regarding achieving PDF/A compliance. This is a live document, so please come back for updated content and feel free to contribute as well.

## LaTeX configuration to embed all fonts
+ Ensure that the options `pdftexDownloadBase14` and `dvipsDownloadBase35` are set to true in your `updmap.cfg` file. In order to ensure that that you are editing the correct file run first `updmap -sys` to see which files are used. 

## LaTeX packages to ensure PDF/A 
+  Modify the documentclass to include pdfa, for example:
```
\documentclass[sigconf, nonacm, pdfa]{acmart}
```
+  In you latex source code use the package `pdfx`. The full documentation of the package is here: https://texdoc.org/serve/pdfx.pdf/0  
```
\usepackage[a-2b]{pdfx})
```` 
+ A recently published guide with more details: https://webpages.tuni.fi/latex/pdfa-guide.pdf 
+ A (slightly older) very detailed how-to guide: https://www.mathstat.dal.ca/~selinger/pdfa/. Note that this guide contains several steps that are not currently required, but they can help establish good practices.

## Adobe Acrobat for PDF/A

Adobe Acrobat can also save as PDF/A, however, note that this does not always mean that the file is compliant. Rather, it means that the file _claims to be compliant_. More checking is typically necessary. 
+ If you use `File > Save as Other > Archival PDF (PDF/A)` this will *not* ensure PDF/A compliance. In fact most of the time this will *not* be sufficient.

### Adobe Acrobat Preflight for PDF/A
+ If you use Adobe Preflight to run a "Convert to PDF/A" profile and the process succeeds this will be sufficient. 
  + In the Creative Cloud Suite, this can be found in Adobe Acrobat under `Edit > Preflight` where you can select the profile "Convert to PDF/A-2b" and click on "Analyze and fix". This will open a new dialogue box that will ask you to give the desired output filename.


# How to test for PDF/A and font compliance.

OK, so you have followed all the above guidelines to make your file compliant. Can you verify with the same tools as the PVLDB Publication Process? To do that, we add below a simple version of the testing suite used during publication.

## PVLDB Vol 17 Testing Scripts
+ Before you start, follow the guidelines in [_tools/INSTALL_TOOLS.md](_tools/INSTALL_TOOLS.md) to install the necessary tools.
+ Once the tools are installed, you can run the two scripts `check_fonts_pdfa.py` to check fonts and PDF/A compliance and `check_format.py` to check other common formatting errors. 
+ Note that these are not exhaustive!
+ Give `python check_fonts_pdfa.py --dir <directory with pdf files to check>` and all files in that folder will be checked for PDF/A and font compliance.
+ Give `python check_format.py --dir <directory with pdf files to check>` and all files in that folder will be checked for common formatting errors.

## Online tools

### Online tools to check for PDF/A compliance
+ https://www.pdfen.com/pdf-a-validator
+ https://pdf.online/validate-pdfa
+ https://avepdf.com/pdfa-validation

### Online tools to convert to PDF/A 
+ https://pdf.online/pdf-to-pdfa
+ https://www.ilovepdf.com/convert-pdf-to-pdfa

### Removing Type 3 fonts (this is a best-effort collection of online links)
Note that typically, if you ensure PDF/A compliance there should be no Type 3 fonts. Just in case, below we have a collection of links solely about removing Type 3 fonts in a more ad hoc manner.
+ https://me.net.nz/post/type3fonts/
+ https://blog.mattoverby.net/2021/07/you-can-remove-type-3-fonts-with.html
+ https://tex.stackexchange.com/questions/18687/how-to-generate-pdf-without-any-type3-fonts
