# Items needed specifically by autotools
AM_FCFLAGS = -Wall -O0 -C -fbacktrace

noinst_PROGRAMS = datetime_tests

datetime_tests_SOURCES = datetime_tests.f90

#datetime_tests$(EXEEXT) : datetime_tests.f90 ../datetime_module.mod
#	$(FC) -I.. $< -o $@ -L.. -ldatetime

CLEANFILES = *.mod

# Mostly unchanged from original upstream Makefile
LIB = ../lib
INCLUDE = ../lib


OBJ = datetime_tests.o

.f90.o:
	$(FC) -c $(AM_FCFLAGS) -I$(INCLUDE) $<

datetime_tests$(EXEEXT): datetime_tests.o
	$(FC) $(FCFLAGS) $(OBJ) -L$(LIB) -ldatetime -o $@

