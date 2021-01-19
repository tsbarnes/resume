PUBLISH_THEME   := stackoverflow
resume_THEME    := stackoverflow
fullstack_THEME := paper
devops_THEME    := stackoverflow
backend_THEME   := class
frontend_THEME  := class

TARGETS = resume fullstack devops backend frontend

resume_SOURCE    = resume.json
fullstack_SOURCE = $(resume_SOURCE) fullstack.json
devops_SOURCE    = $(resume_SOURCE) devops.json
backend_SOURCE   = $(resume_SOURCE) backend.json
frontend_SOURCE  = $(resume_SOURCE) frontend.json

hackmyresume_EXE = ../node_modules/.bin/hackmyresume

all: build

build: $(TARGETS)

.SECONDEXPANSION:
$(TARGETS): $$($$@_SOURCE)
	$(hackmyresume_EXE) BUILD $^ TO ../build/$@.all -t ../node_modules/jsonresume-theme-$($@_THEME)
	$(hackmyresume_EXE) BUILD $^ TO ../build/$@.doc -t positive
	$(hackmyresume_EXE) BUILD $^ TO ../build/$@.txt -t positive

publish: resume.json
	resume publish -t $(PUBLISH_THEME)

export: resume.json resume.html resume.pdf

%.pdf: %.html
	wkhtmltopdf $< $@

%.html: resume.json
	resume export $@ -t $(EXPORT_THEME)
