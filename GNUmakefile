VOC = /opt/voc/bin/voc
mkfile_path := $(abspath $(lastword $(MAKEFILE_LIST)))
mkfile_dir_path := $(shell dirname $(realpath $(firstword $(MAKEFILE_LIST))))
BUILD="build"
build_dir_path := $(mkfile_dir_path)/$(BUILD)
current_dir := $(notdir $(patsubst %/,%,$(dir $(mkfile_path))))
BLD := $(mkfile_dir_path)/build
DPD  =  deps
DPS := $(mkfile_dir_path)/$(DPD)

all: get_deps build_deps build

get_deps:
	mkdir -p $(DPS)
	if [ -d $(DPS)/time ]; then cd $(DPS)/time; git pull; cd -; else cd $(DPS); git clone https://github.com/norayr/time; cd -; fi

build_deps:
	mkdir -p $(BUILD)
	cd $(BUILD)
	make -f $(mkfile_dir_path)/$(DPD)/time/GNUmakefile BUILD=$(BLD)

build:
	cd $(BLD) && $(VOC) -s $(mkfile_dir_path)/src/time.Mod

clean:
	if [ -d "$(BLD)" ]; then rm -rf $(BLD); fi
