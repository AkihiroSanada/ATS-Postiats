#
# A simple Makefile
#

######

MAKE=make

######

PATSCC=$(PATSHOME)/bin/patscc
PATSOPT=$(PATSHOME)/bin/patsopt

######

CATSPARSEMIT=./CATS-parsemit

######

SOURCES_DATS :=
SOURCES_DATS += DATS/atscc2clj_main.dats
SOURCES_DATS += DATS/atscc2clj_emit.dats
SOURCES_DATS += DATS/atscc2clj_emit2.dats

SOURCES_SATS :=
SOURCES_SATS += $(CATSPARSEMIT)/SATS/catsparse.sats

SOURCES_CATS :=
SOURCES_CATS += $(CATSPARSEMIT)/CATS/catsparse_all_dats.c

######
#
all:: ; \
$(MAKE) -C CATS-parsemit all
#
######
#
all:: \
bin_atscc2clj
bin_atscc2clj: \
$(SOURCES_DATS); \
$(PATSCC) \
  -DATS_MEMALLOC_GCBDW -O2 -o bin/atscc2clj \
  $(SOURCES_DATS) $(SOURCES_SATS) $(SOURCES_CATS) -lgc
#
######
#
npm:: bin_atscc2clj
npm:: ; $(CPF) catsparse_sats.c atscc2clj_*_dats.c npm/CATS/.
#
######

CPF=cp -f
RMF=rm -f

######
#
testall:: all
testall:: cleanall
#
######

clean:: ; $(RMF) *~
clean:: ; $(RMF) *_?ats.o
clean:: ; $(RMF) *_?ats.c

######
#
cleanall:: clean
#
cleanall:: ; $(RMF) ./bin/atscc2clj
cleanall:: ; $(RMF) ./npm/CATS/catsparse_sats.c
cleanall:: ; $(RMF) ./npm/CATS/atscc2clj_*_dats.c 
#
###### end of [Makefile] ######
