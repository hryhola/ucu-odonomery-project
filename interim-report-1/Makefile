MAIN = LA-report-template-2026

.PHONY: pdf watch open clean
pdf:   ; latexmk $(MAIN).tex && cp build/$(MAIN).pdf .
watch: ; latexmk -pvc -view=none $(MAIN).tex   # rebuild on save
open:  ; open $(MAIN).pdf
clean: ; latexmk -C $(MAIN).tex; rm -rf build $(MAIN).pdf
