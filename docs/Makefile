all: enunciado.pdf descricao.pdf

%.pdf: %.tex *.tex
	echo $@
	ln -fs $< corpo.tex
	pdflatex -halt-on-error -interaction=nonstopmode cabecalho.tex \
		&& mv cabecalho.pdf $@

clean:
		rm -f *.{aux,log,nav,out,snm,toc,vrb,c.tex,c.log}

cleanall:
		rm -f *.{aux,log,nav,out,snm,toc,vrb,c.tex,c.log} enunciado.pdf descricao.pdf
