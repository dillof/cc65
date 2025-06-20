# ---- Display info during parsing phase ----
SILENT:=$(findstring s,$(word 1, $(MAKEFLAGS)))
ifneq ($(SILENT),s)
    $(info Using Makefile: $(realpath $(firstword $(MAKEFILE_LIST))) $(MAKECMDGOALS))
endif

# top-level Makefile for the regression tests

ifneq ($(shell echo),)
  CMD_EXE = 1
endif

ifdef CMD_EXE
  RMDIR = -rmdir /s /q $(subst /,\,$1)
else
  RMDIR = $(RM) -r $1
endif

WORKDIR = ../testwrk

.PHONY: test continue mostlyclean clean success_message

test:
	@$(MAKE) mostlyclean
	@$(MAKE) continue

continue:
	@$(MAKE) -C asm all
	@$(MAKE) -C dasm all
	@$(MAKE) -C val all
	@$(MAKE) -C ref all
	@$(MAKE) -C err all
	@$(MAKE) -C standard all
	@$(MAKE) -C standard_err all
	@$(MAKE) -C misc all
	@$(MAKE) -C todo all
	@$(MAKE) success_message

success_message:
	$(info ###################################)
	$(info ### validation suite successful ###)
	$(info ###################################)

mostlyclean:
	@$(MAKE) -C asm clean
	@$(MAKE) -C dasm clean
	@$(MAKE) -C val clean
	@$(MAKE) -C ref clean
	@$(MAKE) -C err clean
	@$(MAKE) -C standard clean
	@$(MAKE) -C standard_err clean
	@$(MAKE) -C misc clean
	@$(MAKE) -C todo clean

clean: mostlyclean
	@$(call RMDIR,$(WORKDIR))
