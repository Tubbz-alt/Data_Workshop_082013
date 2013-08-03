#CC=mpicc
#FC=mpif90
#ADIOS_DIR = /opt/adios/1.5.0
CC=cc
FC=ftn
ADIOS_DIR = /sw/xk6/adios/1.5.0/cle4.0_pgi12.10.0
ADIOS_INC = $(shell ${ADIOS_DIR}/bin/adios_config -c)
ADIOS_CLIB = $(shell ${ADIOS_DIR}/bin/adios_config -l)
GPP = ${ADIOS_DIR}/bin/gpp.py


default: all
all: adios_global_no_xml

adios_global_no_xml: adios_global_no_xml.c
	${CC}  -g -o adios_global_no_xml ${ADIOS_INC} adios_global_no_xml.c ${ADIOS_CLIB}

clean:
	rm -f *.o *.mod *.fh core.* fort.* *.png *.bp 
	rm -f adios_global_no_xml 

