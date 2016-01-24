PUBLISH_THEME := elegant
EXPORT_THEME  := class

all: publish export

publish: resume.json
	resume publish -t $(PUBLISH_THEME)

export: resume.json resume.html resume.pdf

%.pdf: %.html
	wkhtmltopdf $< $@

%.html: resume.json
	resume export $@ -t $(EXPORT_THEME)

