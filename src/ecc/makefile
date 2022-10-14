# There are 2 empty files 'pass1'  and 'pass2' whose timestamp decides what to
# do.
#
# pass1:
# 	Make a latex run and collect all references and citations and call
# 	bibtex to extract the references from the bibliography library. Finally
# 	touch the file 'pass1'.
#
# 	'pass1' does not depend on anything. It is run when triggered.
#
# pass2:
# 	Make a 2nd latex run and touch the file 'pass2'. The pass2 depends on
# 	pass1 i.e. if pass1 has not been touched after pass2, then nothing is
# 	done.
#
# 	'pass2'  either does nothing or runs 'pass1' and 'pass2'

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


run-latex = (cd $(build-dir); pdflatex ecc.tex)

# make the pdf
.PHONY: pdf
pdf:
	cp $(source-files) $(build-dir); $(run-latex)


# Create pdf up to pass2. Make pass1 if not yet run on the current version of
# the sources.
.PHONY: pass2
pass2: $(build-dir)pass2


# Create pdf up to pass1 if any source has been changed.
.PHONY: pass1
pass1: $(build-dir)pass1



# Make an extra latex run. Necessary after the first two passes and if
# citations or the bibliography have been changed.
.PHONY: extra
extra:
	$(run-latex)



# Clean the build directory
.PHONY: clean
clean:
	rm $(build-dir)*



# Create 'pass1' file in the build directory, if sources have been changed.
$(build-dir)pass1: $(source-files) makefile
	cp $(source-files) $(build-dir); \
	$(run-latex);                    \
	(cd $(build-dir); bibtex ecc);   \
	touch $(build-dir)pass1



# Create 'pass2' file in the build directory, if 'pass1' file is more recent.
$(build-dir)pass2: $(build-dir)pass1
	$(run-latex);   \
	touch $(build-dir)pass2

