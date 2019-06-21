NAME = presentation
PLANT_OUTDIR = instance
PLANT_SRCS = $(wildcard *.plantuml)
PLANT_IMGS = $(patsubst %.plantuml,$(PLANT_OUTDIR)/%.svg,$(PLANT_SRCS))

.PHONY: help
help:  ## Prints this help menu
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | \
		awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'

.PHONY: setup
setup: poetry.lock fonts  ## Initialize project, install dependencies

.PHONY: build-pdf
build-pdf: $(NAME).pdf  ## Build the PDF assets

.PHONY: build-zip
build-zip: $(NAME).zip  ## Build a ZIP version of the presentation

.PHONY: build-assets
build-assets: $(NAME).assets  ## Build the presentation assets

.PHONY: plantuml
plantuml: $(PLANT_IMGS)  ## Build any plantuml diagrams

.PHONY: serve
serve: $(NAME).rst setup plantuml  ## Serve in development mode
	poetry run hovercraft $<

.PHONY: clean
clean:  ## Clean up any assets installed during development
	-rm -r $(NAME).assets
	-rm -r fonts

%.zip: %.assets
	zip -r $@ $<

%.pdf: %.rst poetry.lock fonts $(PLANT_IMGS)
	pandoc $< -o $@ \
		-V geometry:"paperheight=11in, paperwidth=8.5in, margin=0.75in" \
		--filter=pandoc-latex-newpage

%.assets: %.rst poetry.lock fonts $(PLANT_IMGS)
	poetry run hovercraft $< $@

$(PLANT_OUTDIR)/%.svg: %.plantuml
	plantuml -tsvg -o $(PLANT_OUTDIR) $<

poetry.lock: pyproject.toml
	poetry install

pyproject.toml:
	poetry init --no-interaction
	poetry add hovercraft
	poetry add pandoc-latex-newpage

fonts:
	wget -O $@.zip https://github.com/mozilla/Fira/archive/4.202.zip
	unzip -d $@ $@.zip
	rm $@.zip
