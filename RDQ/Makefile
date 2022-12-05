# Makefile for Radar Data Acquisition Package (RDQ)
# Owain Davies 04/02/2004

# This is the base path for the package
ROOTPATH=.

# This is where the bits and pieces are kept
SRCDIR = $(ROOTPATH)/src
INCDIR = $(ROOTPATH)/include
LIBDIR = $(ROOTPATH)/lib
BINDIR = $(ROOTPATH)/bin




CC     = gcc
CFLAGS = -Wall -O3 -ffast-math -I$(INCDIR)
LIBS   = -lm

# The master header file
INC = $(INCDIR)/RDQ.h

# Top level rule
all : dirs $(LIBDIR)/librdq12.a

# The main library
$(LIBDIR)/librdq12.a : $(BINDIR)/RDQ_DataAcquisition.o
	ar r $@ $(BINDIR)/RDQ_DataAcquisition.o

$(BINDIR)/RDQ_DataAcquisition.o : $(SRCDIR)/RDQ_DataAcquisition.c $(INC)
	$(CC) $(CFLAGS) -o $@ -c $(SRCDIR)/RDQ_DataAcquisition.c
	
dirs:
	[ -d $(LIBDIR) ] || mkdir -p $(LIBDIR)
	[ -d $(BINDIR) ] || mkdir -p $(BINDIR)

clean :
	$(RM) $(BINDIR)/*.[doa]
	$(RM) $(LIBDIR)/*.[doa]
