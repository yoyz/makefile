.SUFFIXES:       
PLATFORM:=  DEB

include $(PWD)/Makefile.$(PLATFORM)

AUTHOR := peyrardj
TITLE  := test


# Directory

DEBDIRS := ../src/main/

# Files

DEBFILES := hello.o

COMMONFILES	:=


#---------------------------------------------------------------------------------    
# TARGET is the name of the output            
# BUILD is the directory where object files & intermediate files will be placed
#---------------------------------------------------------------------------------        
TARGET          :=      $(TITLE)            
BUILD           :=      build$(PLATFORM)
SOURCES         :=      $($(PLATFORM)DIRS) $(COMMONDIRS) 
INCLUDES        :=        



ifneq ($(BUILD),$(notdir $(CURDIR)))     

export OUTPUT   :=      $(CURDIR)/$(TARGET)
export VPATH    :=      $(foreach dir,$(SOURCES),$(CURDIR)/$(dir))
export DEPSDIR  :=      $(CURDIR)/$(BUILD)
export LD       :=      $(CXX)            
export OFILES   :=      $(COMMONFILES) $($(PLATFORM)FILES)
export OBJS 	:= 	$(OFILES)        
export INCLUDE  :=      $(foreach dir,$(INCLUDES),-I$(CURDIR)/$(dir)) 	\
                        $(foreach dir,$(LIBDIRS),-I$(dir)/include) -I$(CURDIR)/$(BUILD) \
			-I$(CURDIR)/$(BUILD)
export LIBPATHS :=      $(foreach dir,$(LIBDIRS),-L$(dir)/lib) 


.PHONY: $(BUILD) clean    

$(BUILD):    
	[ -d $@ ] || mkdir -p $@
	make --no-print-directory -C $(BUILD) -f $(PWD)/Makefile

clean:                                                                     
	@echo clean ...                                                    
	@rm -fr $(OUTPUT).$(EXTENSION) $(BUILD) *.elf *.gxb *.fxe          
else    	                                                                           


all: $(OUTPUT).$(EXTENSION) 


$(OUTPUT).deb-exe       :       $(OFILES)
	$(LD) $(LDFLAGS) -o $@ $(OFILES) $(LIBS)

%.o: %.c
	echo $(notdir $<)
	$(CC) -MMD -MF $(DEPSDIR)/$*.d $(CFLAGS) -c $< -o $@
	$(adjustdepends)

-include $(DEPENDS)



endif
