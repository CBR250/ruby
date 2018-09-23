first_rule: all

all: build install

PACKAGE_NAME := readline-7.0
PACKAGE_DIR := readline-7.0

# Configuration
PACKAGE_CONF := \
    --prefix=$(CURDIR)/../../OBJ/ \

test_directory:
	if [ ! -d $(CURDIR)/../../TARGET ]; then \
	   mkdir $(CURDIR)/../../TARGET/; \
	fi
	if [ -d $(CURDIR)/../../TARGET/$(PACKAGE_DIR) ]; then \
	       echo "Folder existed"; \
	else \
	       tar xvf $(CURDIR)/$(PACKAGE_NAME).tar.gz -C $(CURDIR)/../../TARGET/; \
	       patch -Np1 -d $(CURDIR)/../../TARGET/readline-7.0 < $(CURDIR)/../../PATCH/readline/shlib_Makefile.patch; \
	       patch -Np1 -d $(CURDIR)/../../TARGET/readline-7.0 < $(CURDIR)/../../PATCH/readline/support_shlib-install.patch; \
	       patch -Np1 -d $(CURDIR)/../../TARGET/readline-7.0 < $(CURDIR)/../../PATCH/readline/support_shobj-conf.patch; \
	fi

build_lib: test_directory
	cd $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/ && ./configure $(PACKAGE_CONF); \

build: build_lib
	$(MAKE) -C $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/ all

pre_install_check:
	if [ ! -d $(CURDIR)/../../OBJ/lib ]; then \
	    mkdir -p $(CURDIR)/../../OBJ/lib; \
	fi
	if [ ! -d $(CURDIR)/../../OBJ/bin ]; then \
	    mkdir -p $(CURDIR)/../../OBJ/bin; \
	fi

install: pre_install_check
	$(MAKE) -C $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/ install
	
config_rule:

clean_rule:

uninstall_rule:
