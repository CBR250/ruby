CURDIR=$(shell pwd)
PACKAGE_VERSION :=
PACKAGE_DIR :=
PACKAGE_CONF :=
first_rule: all

all: build

build:
	$(MAKE) -C $(CURDIR)/PACKAGE/zlib          first_rule
	$(MAKE) -C $(CURDIR)/PACKAGE/readline      first_rule
	$(MAKE) -C $(CURDIR)/PACKAGE/openssl       first_rule
	$(MAKE) -C $(CURDIR)/PACKAGE/ruby          first_rule

config_rule:

install_rule install:

clean_rule distclean clean:

uninstall_rule uninstall:
