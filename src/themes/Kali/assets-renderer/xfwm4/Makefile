include ../../../Makefile.inc

ASSETS=assets*.svg
INDEX=assets.txt
THEMES_DIR=../../../../../share/themes/

.PHONY: build clean

build: $(ASSETS)
	for src_file in $(ASSETS); \
	do \
		variant=$$(basename $${src_file%.svg}) ; \
		mkdir -p $$variant $$variant@2 ; \
		for i in $$(xargs < $(INDEX)) ; \
		do \
			echo ; \
			echo Rendering $$variant/$$i.png ; \
			$(INKSCAPE) --export-id=$$i \
			            --export-id-only \
			            --export-png=$$variant/$$i.png $$src_file > /dev/null 2>&1 \
			&& $(OPTIPNG) $$variant/$$i.png ; \
			echo ; \
			echo Rendering $$variant@2/$$i.png ; \
			$(INKSCAPE) --export-id=$$i \
			            --export-dpi=192 \
			            --export-id-only \
			            --export-png=$$variant@2/$$i.png $$src_file > /dev/null 2>&1  \
			&& $(OPTIPNG) $$variant@2/$$i.png ; \
		done ; \
	done
	mkdir -p $(THEMES_DIR)Kaliish-orange$(VARIANT)-Light/xfwm4/
	mkdir -p $(THEMES_DIR)Kaliish-orange$(VARIANT)-Dark/xfwm4/
	mkdir -p $(THEMES_DIR)Kaliish-orange$(VARIANT)-Light-xHiDPI/xfwm4/
	mkdir -p $(THEMES_DIR)Kaliish-orange$(VARIANT)-Dark-xHiDPI/xfwm4/
	cp assets-light/* $(THEMES_DIR)Kaliish-orange$(VARIANT)-Light/xfwm4/
	cp assets-dark/* $(THEMES_DIR)Kaliish-orange$(VARIANT)-Dark/xfwm4/
	cp assets-light@2/* $(THEMES_DIR)Kaliish-orange$(VARIANT)-Light-xHiDPI/xfwm4/
	cp assets-dark@2/* $(THEMES_DIR)Kaliish-orange$(VARIANT)-Dark-xHiDPI/xfwm4/

clean:
	-rm -r assets-light assets-light@2 assets-dark assets-dark@2
