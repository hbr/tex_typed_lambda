# Generate a pdf from scratch:
#     make pdf                  1st pass collect all references
#     make bib                  extract from bib database
#     make pdf                  2nd pass update references


build-dir = ../../_build/ecc/

source-files = \
	ecc.tex \
	ecc_macros.tex \
	ecc_intro.tex \
	ecc_calculus.tex \
	ecc_subtyping.tex \
	ecc_confluence.tex \
	ecc_typing.tex \
	ecc_quasinormal.tex \
	ecc_normal.tex \
	ecc_thoughts.tex \
	ecc_references.tex



# Run pdflatex and generate the pdf file (only once)
# Run it twice to get crossreferences correct if new labels have been
# introduced.
.PHONY: pdf
pdf: mk-build-dir
	rm $(build-dir)*.tex;  \
	cp $(source-files) $(build-dir); \
	(cd $(build-dir); pdflatex ecc.tex)


# Extract citations for the bib database. Run always, if a new citation has been
# added.
.PHONY: bib
bib: mk-build-dir
	(cd $(build-dir); bibtex ecc)



# Make the build directory, if necessary
.PHONY: mk-build-dir
mk-build-dir:
	test -d "$(build-dir)" || mkdir -p $(build-dir)
