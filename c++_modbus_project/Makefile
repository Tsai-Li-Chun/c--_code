# ------------------------------------------------
#	Generic Makefile (based on gcc)
#	Author	：Tsai,Li-chun
#	OS		：Ubuntu20.04 TLS
#	Brief	：c++ modbus project
# ------------------------------------------------


############################################################################
#	target
######################################
target  = modbus

############################################################################
#	building variables
######################################
# optimization
OPT = -O0

############################################################################
#	project file paths
#######################################
# source code file paths
src_path = src/
# headle file paths
inc_path = -Iinc/ \
		   -I/usr/local/include/modbus
# object file paths
obj_path = build/

#######################################
# link script & libraries
#######################################
# libraries
libs = -L/usr/local/lib -lmodbus

############################################################################
#	compile gcc flags
#######################################
# Generate dependency information
CFLAGS = -std=c++11 -O0 -MMD -MP $(inc_path)

############################################################################
#	source code
######################################
c_sources = \
	src/main.cpp \
	src/Modbus_Handshake.cpp \

############################################################################
#	object file
######################################
obj_tmp	= $(subst $(src_path), $(obj_path), $(c_sources))
obj     = $(patsubst %.cpp, %.o, $(obj_tmp))

############################################################################
#	dependency file
######################################
dep     = $(patsubst %.o, %.d, $(obj))

############################################################################
# default action: build all
######################################
all: $(target)
	@echo "target $< complete"
$(target): $(obj)
	g++ $^ -o $@ $(libs)

############################################################################
# build the application
#######################################
-include $(dep)
${obj_path}%.o: ${src_path}%.cpp Makefile
	g++ $(CFLAGS) -c $< -o $@


############################################################################
# .PHONY
#######################################
.PHONY: clean
clean:
	rm -f *.o *.d $(target)
	rm -f $(obj_path)*.o $(obj_path)*.d
