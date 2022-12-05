# Makefile for Radar NetCDF Package (RNC)
# Owain Davies 04/02/2004

# This is the base path for the package
ROOTPATH=.

# This is where the bits and pieces are kept
SRCDIR = $(ROOTPATH)/src
LIBDIR = $(ROOTPATH)/lib
BINDIR = $(ROOTPATH)/bin
INCDIR = $(ROOTPATH)/include

CC     = gcc
CFLAGS = -Wall -O3 -ffast-math -I$(INCDIR)
LIBS   = -lm -lpthread -lrt

# The master header file
INC = $(INCDIR)/REL.h

# Top level rule
all : dirs $(LIBDIR)/librel.a
test: test_REL

# The main library
$(LIBDIR)/librel.a : $(BINDIR)/REL_SerialMessage.o
	ar r $@ $(BINDIR)/REL_SerialMessage.o

$(BINDIR)/REL_SerialMessage.o : $(SRCDIR)/REL_SerialMessage.c $(INC)
	$(CC) $(CFLAGS) -c $(SRCDIR)/REL_SerialMessage.c -o $(BINDIR)/REL_SerialMessage.o

test_REL : $(SRCDIR)/test_REL.c $(SRCDIR)/REL_SerialMessage.c $(INC)
	$(CC) $(CFLAGS) -o $@ $(SRCDIR)/test_REL.c $(BINDIR)/REL_SerialMessage.o $(LIBS)
	
dirs:
	[ -d $(LIBDIR) ] || mkdir -p $(LIBDIR)
	[ -d $(BINDIR) ] || mkdir -p $(BINDIR)
	

clean :
	$(RM) $(BINDIR)/*.[doa]
	$(RM) $(LIBDIR)/*.[doa]
