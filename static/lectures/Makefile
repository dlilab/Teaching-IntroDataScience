ALL: 01_about/presentation.html 02_proj_cycle/presentation.html 03_tools/presentation.html 04_git/presentation.html \
05_github/presentation.html 06_rmd/presentation.html 08_r_basic/presentation.html \
09_r_basic/presentation.html 10_condition/presentation.html 11_loops/presentation.html \
12_strings/presentation.html 13_api/presentation.html 14_data_in_out/presentation.html \
15_data_manipulation/presentation.html 16_data_visualization/presentation.html \
17_EDA/presentation.html 18_regression/presentation.html 19_regression_2/presentation.html \
20_spatial_analysis/presentation.html 20_functions/presentation.html \
21_R_pkg/presentation.html 22_make/presentation.html


OStype := $(shell uname -s)

ifeq ($(OStype), Linux)
	   view = evince
endif

ifeq ($(OStype), Darwin)
	   view = open
endif

%.pdf: %.tex
	cd $(@D); if [[ $< == *notes.tex ]]; then xelatex $(<F); fi
	$(view) $@

%.pdf: %.Rmd
	if [[ $< == *notes* ]]; then Rscript -e 'rmarkdown::render("$<", output_format = "bookdown::pdf_document2")'; fi
	$(view) $@

%.html: %.Rmd
	if [[ $< == *presentation* ]] ; then Rscript -e 'rmarkdown::render("$<")'; fi
			
clean:
	rm -fv */*.aux */*.log */*.toc */*.blg */*.bbl */*.synctex.gz
	rm -fv */*.nav */*.aux */*.snm 
	rm -fv */*.out */*.bcf */*blx.bib */*.run.xml
	rm -fv */*.fdb_latexmk */*.fls
