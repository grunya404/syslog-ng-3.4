SCL_SUBDIRS = system
SCL_CONFIGS = scl.conf modules.conf syslog-ng.conf
EXTRA_DIST = ./scl.conf $(SCL_SUBDIRS)

scldir = $(datarootdir)/include/scl

install-data-local:
	for cfg in $(SCL_CONFIGS); do \
		if [ -f $(DESTDIR)/$(sysconfdir)/$${cfg} ]; then \
			echo "Not overwriting existing configuration file, you might want to upgrade manually: $${cfg}"; \
		else \
			$(install_sh_DATA) $(srcdir)/$${cfg}  $(DESTDIR)/$(sysconfdir); \
		fi; \
	done
	(cd $(srcdir); tar cf - $(SCL_SUBDIRS)) | (cd $(DESTDIR)/$(scldir) && tar xf -)