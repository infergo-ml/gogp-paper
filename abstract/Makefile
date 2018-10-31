all: paper.pdf paper.aux

PDFLATEX=pdflatex

%.aux: %.tex
	$(PDFLATEX) ${basename $<}

%.bbl: %.aux
	bibtex ${basename $<}

%.pdf: %.bbl
	$(PDFLATEX) ${basename $<}
	$(PDFLATEX) ${basename $<}

paper.pdf: paper.tex \
	refs.bib

arxiv: for-arxiv.zip
for-arxiv.zip: paper.pdf paper.bbl
	-rm for-arxiv.zip
	zip for-arxiv.zip \
    paper.tex paper.bbl \
	acmart.cls

clean:
	rm -f *.aux *.log *.bbl *.blg

distclean: clean
	rm -f paper.pdf
