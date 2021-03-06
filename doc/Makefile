## Put this Makefile in your project directory---i.e., the directory
## containing the paper you are writing. Assuming you are using the
## rest of the toolchain here, you can use it to create .html, .tex,
## and .pdf output files (complete with bibliography, if present) from
## your markdown file.
## -	Change the paths at the top of the file as needed.
## -	Using `make` without arguments will generate html, tex, and pdf
## 	output files from all of the files with the designated markdown
##	extension. The default is `.md` but you can change this.
## -	You can specify an output format with `make tex`, `make pdf` or
## - 	`make html`.
## -	Doing `make clean` will remove all the .tex, .html, and .pdf files
## 	in your working directory. Make sure you do not have files in these
##	formats that you want to keep!

## Markdown extension (e.g. md, markdown, mdown).
MEXT = md

## All markdown files in the working directory
SRC = $(sort $(wildcard *.$(MEXT)))

## Location of your working bibliography file
BIB = ./references.bib

## CSL stylesheet (located in the csl folder of the PREFIX directory).
CSL = ieee


PDFS=$(SRC:.md=.pdf)
HTML=$(SRC:.md=.html)
TEX=$(SRC:.md=.tex)
TEMPLATE=paper.template


all:	proposal

proposal: $(SRC)
	pandoc -r markdown+simple_tables+table_captions+yaml_metadata_block -s -S --latex-engine=pdflatex --template=$(TEMPLATE) --filter pandoc-citeproc --csl=$(CSL).csl --bibliography=$(BIB) -V geometry:margin=1in -o proposal.pdf $(SRC)

clean:
	rm -f *.html *.pdf *.tex
