manuscript = spectral-elements-notes
references = $(wildcard *.bib)
latexopt   = -halt-on-error -file-line-error

.DEFAULT_GOAL := pdf

pdf: $(manuscript).tex $(references)
	pdflatex $(latexopt) $(manuscript)
	biber $(manuscript)
	pdflatex $(latexopt) $(manuscript)
	pdflatex $(latexopt) $(manuscript)
	$(MAKE) clean

pdf-dbg: $(manuscript).tex $(references)
	pdflatex $(latexopt) $(manuscript)
	bibtex $(manuscript)
	pdflatex $(latexopt) $(manuscript)
	pdflatex $(latexopt) $(manuscript)

epub:
	latex $(latexopt) $(manuscript)
	bibtex $(manuscript)
	mk4ht htlatex $(manuscript).tex 'xhtml,charset=utf-8,pmathml' ' -cunihtf -utf8 -cvalidate'
	ebook-convert $(manuscript).html $(manuscript).epub

clean:
	rm -f *.dvi *.toc *.aux *.out *.log *.bbl *.blg *.spl *~ *.zip \
	      *.acn *.glo *.ist *.epub *.fdb_latexmk *.lof *.fls *.lot \
        *.bcf *.xml

.PHONY: pdf pdf-dbg epub clean

