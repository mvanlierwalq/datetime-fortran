# Items needed specifically by autotools
AM_FCFLAGS = -Wall -O0 -C -fbacktrace

include_HEADERS = datetime_module.mod

lib_LIBRARIES = libdatetime.a

libdatetime_a_SOURCES = datetime.f90 mod_datetime.f90 mod_timedelta.f90 \
	mod_strftime.f90 mod_clock.f90 mod_constants.f90

CLEANFILES = *.mod

# Mostly unchanged from original upstream Makefile
OBJS = datetime.o mod_clock.o  mod_datetime.o mod_timedelta.o mod_strftime.o  mod_constants.o

.f90.o:
	$(FC) -c $(AM_FCFLAGS) $<

libdatetime.a : datetime.o
	ar ruv libdatetime.a $(OBJS)

datetime_module.mod : datetime.o

#install-exec-hook : datetime_module.mod
#	cp datetime_module.mod $(libdir)

#uninstall-hook :
#	rm $(libdir)/datetime_module.mod

datetime.o :      datetime.f90 mod_clock.o mod_datetime.o mod_strftime.o mod_timedelta.o
mod_clock.o:     mod_clock.f90 mod_datetime.o mod_timedelta.o
mod_datetime.o:  mod_datetime.f90 mod_constants.o mod_strftime.o mod_timedelta.o
mod_timedelta.o: mod_timedelta.f90 
mod_strftime.o:  mod_strftime.f90 
mod_constants.o: mod_constants.f90 
