all: DA.glo
	rubber -d DA &>/dev/null

DA.glo:
	@echo "compiling DA.tex ..."
	@pdflatex DA.tex &>/dev/null
	@echo "building glossary ..."
	@makeglossaries DA &>/dev/null

spellcheck:
	aspell check -t DA.tex

clean:
	rubber -d --clean DA
	@rm -rf *.aux *.pdf *~ *.log *.bbl *.blg *.lol &>/dev/null
	@rm *.glo *.gls *.ist *.glg &>/dev/null

view: all
	evince DA.pdf

