#FC=mpif90
FC=ftn
LINKER=${FC}
#ADIOS_DIR = /opt/adios/1.5.0
ADIOS_DIR = /sw/xk6/adios/1.5.0/cle4.0_pgi12.10.0
ADIOS_INC = $(shell ${ADIOS_DIR}/bin/adios_config -c -f)
ADIOS_FLIB = $(shell ${ADIOS_DIR}/bin/adios_config -l -f)
ADIOSREAD_FLIB := $(shell ${ADIOS_DIR}/bin/adios_config -l -f -r)
ADIOSREAD_SEQ_CLIB = $(shell ${ADIOS_DIR}/bin/adios_config -l -r -s)
GPP = ${ADIOS_DIR}/bin/gpp.py


default: all
all: writer reader map

writer: writer.F90 gwrite_writer.fh
	${FC}   -g -c -o writer.o ${ADIOS_INC} writer.F90
	${LINKER}   -g -o writer writer.o ${ADIOS_FLIB}

gwrite_writer.fh: writer.xml
	${GPP} writer.xml

reader: reader.F90 
	${FC}   -g -c -o reader.o ${ADIOS_INC} reader.F90
	${LINKER}   -g -o reader reader.o ${ADIOSREAD_FLIB} 

map: map.c
	${CC}  -g -o map ${ADIOS_INC} map.c ${ADIOSREAD_SEQ_CLIB}

clean:
	rm -f *.o *.mod *.fh core.* fort.* *.png
	rm -f writer reader map writer*.bp writer*.h5 writer*.nc

