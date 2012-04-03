#DEBUG   = -nbs -C -d2
#FFLAGC  = -g
#FFLAGC  = -O
opt     = -O2 -ip -xSSE4.2 -openmp -parallel 
# profile = -stack:32000000
obj     = tetr
obj1    = get_forces
ildir   =  
#LIBS    = /Applications/Absoft11.0/lib/libU77.a
# LIBS    = -L/Applications/Absoft11.0/lib64/ -lU77

MKL_PATH = $(INTEL_MKL_HOME)/lib/intel64
IFC_PATH = $(INTEL_IFORT_HOME)/lib/intel64
 
LIBS = $(IFC_PATH)/libiomp5.a -lpthread

input   = 

CFLAGC  = -O2 -ip xSSE4.2 -openmp -parallel 

# FCOMPL  = af90  $(DEBUG) 
#FCOMPL  = ifort -Vaxlib $(DEBUG) 
#FCOMPL  = ifc -Vaxlib $(DEBUG) 
#FCOMPL  = g77
FCOMPL = ifort
CCOMPL  = icc

# list of other directories for source files
.PREFIXES: .

.SUFFIXES:
.SUFFIXES: .f .c .s .o .fil

.f.o:
	$(FCOMPL) -c $(ildir) $(FFLAGC) $(opt) $(profile) $<

OBJECTS = tetrag1.o applica.o lattice.o point_gr.o coulomb.o add_rem.o wyckoff_int.o\
    mol_vibr.o eig_vibr.o input_tetr.o move_atoms.o get_best_ai.o change.o change_tools.o make_fcm.o\
    tools.o tools_strings.o cluster.o permut.o orbita.o do_vibr.o do_cond.o do_irrep.o ttag.o \
     solve_vibr.o devices.o crystal_vibr.o hat.o lattice_space.o build_spacegroup.o bsse.o move_tip.o

OBJECTS1 = get_forces.o

INLINE  = 

APPLIC: $(INLINE) $(OBJECTS)  $(OBJECTS1)  $(OBJECTS2)  $(OBJECTS3)
	$(FCOMPL) $(FFLAGC) $(profile) -o $(obj)  $(OBJECTS)  $(LIBS)
	$(FCOMPL) $(FFLAGC) $(profile) -o $(obj1)  $(OBJECTS1)  $(LIBS)

test:
	@echo START TEST ON $(input) , opt = $(opt)
	@echo start test on $(input) , opt = $(opt) >> TIME.LOG
	@date >> TIME.LOG
	@( time $(obj) < $(input) > $(input).out ) 2>> TIME.LOG
	@echo - - - - - - - - - - - >> TIME.LOG

clean:
	@rm -f $(INLINE) $(OBJECTS) $(OBJECTS1) $(OBJECTS2) $(OBJECTS3)

# include file dependencies

tetrag1.o applica.o lattice.o point_gr.o coulomb.o add_rem.o \
mol_vibr.o eig_vibr.o input_tetr.o move_atoms.o get_best_ai.o change.o change_tools.o \
tools.o cluster.o permut.o orbita.o do_vibr.o do_cond.o crystal_vibr.o\
devices.o do_irrep.o solve_vibr.o make_fcm.o crystal_vibr.o move_tip.o : real8.inc tetr_param.inc sym_par.inc space.inc

cluster.o change.o move_tip.o : lists.inc

lattice_space.o build_spacegroup.o bsee.o ttag.o : real8.inc

add_rem.o applica.o change.o change_tools.o cluster.o coulomb.o do_irrep.o eig_vibr.o input_tetr.o \
devices.o lattice.o make_fcm.o  mol_vibr.o move_atoms.o point_gr.o tetrag1.o \
crystal_vibr.o move_tip.o : tetrag1.inc space.inc

lattice_space.o bsse.o : tetrag1.inc 

lattice_space.o build_spacegroup.o applica.o change.o change_tools.o devices.o  \
do_irrep.o do_vibr.o eig_vibr.o move_atoms.o lattice.o make_fcm.o \
mol_vibr.o permut.o orbita.o point_gr.o solve_vibr.o tetrag1.o crystal_vibr.o wyckoff_int.o : pgroup.inc pgroup_base.inc

do_cond.o do_irrep.o do_vibr.o eig_vibr.o make_fcm.o mol_vibr.o orbita.o permut.o solve_vibr.o \
crystal_vibr.o : symgenv.inc

input_tetr.o tetrag1.o devices.o : mendeleev.inc

applica.o input_tetr.o tetrag1.o bsse.o : siesta.inc

do_irrep.o mol_vibr.o eig_vibr.o solve_bivr.o make_fcm.o  crystal_vibr.o : working.inc

eig_vibr.o make_fcm.o : matrix.inc

devices.o do_irrep.o eig_vibr.o mol_vibr.o orbita.o point_gr.o tetrag1.o crystal_vibr.o : systema.inc

make_fcm.o : atom_info.inc

hat.o : whereis.inc build.hat

move_tip.o : afm.inc

