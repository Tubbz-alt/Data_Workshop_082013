#FC=mpif90
#ADIOS_DIR = /opt/adios/1.5.0
FC=ftn
ADIOS_DIR = /sw/xk6/adios/1.5.0/cle4.0_pgi12.10.0
ADIOS_INC = $(shell ${ADIOS_DIR}/bin/adios_config -c)
ADIOS_FLIB = $(shell ${ADIOS_DIR}/bin/adios_config -lf)
GPP = ${ADIOS_DIR}/bin/gpp.py


default: all
all: writer_noxml

writer_noxml: writer_noxml.F90 
	${FC} -g -c -o writer_noxml.o ${ADIOS_INC} writer_noxml.F90
	${FC} -g -o writer_noxml writer_noxml.o ${ADIOS_FLIB}

clean:
	rm -f *.o *.mod *.fh core.* fort.* *.png *.bp 
	rm -f writer_noxml

