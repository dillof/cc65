# ---- Display info during parsing phase ----
SILENT:=$(findstring s,$(word 1, $(MAKEFLAGS)))
ifneq ($(SILENT),s)
    $(info Using Makefile: $(realpath $(firstword $(MAKEFILE_LIST))) $(MAKECMDGOALS))
endif


.PHONY: atari gamate zlib

util: atari gamate zlib

all: util

atari:
	@$(MAKE) -C atari --no-print-directory $@
gamate:
	@$(MAKE) -C gamate --no-print-directory $@
zlib:
	@$(MAKE) -C zlib --no-print-directory $@

mostlyclean clean:
	@$(MAKE) -C atari --no-print-directory $@
	@$(MAKE) -C gamate --no-print-directory $@
	@$(MAKE) -C zlib --no-print-directory $@

install zip:


