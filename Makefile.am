NULL =

SUBDIRS=po

autostartdir = $(sysconfdir)/xdg/autostart
autostart_in_files = user-dirs-update-gtk.desktop.in
autostart_DATA = $(autostart_in_files:.desktop.in=.desktop)

@INTLTOOL_DESKTOP_RULE@

gsettingsschema_in_files = org.gnome.xdg-user-dirs.gschema.xml.in
gsettings_SCHEMAS = $(gsettingsschema_in_files:.xml.in=.xml)
.PRECIOUS: $(gsettings_SCHEMAS)

@INTLTOOL_XML_NOMERGE_RULE@

@GSETTINGS_RULES@

INCLUDES =					\
	-I$(top_srcdir)				\
	-I$(top_builddir)			\
	-DLOCALEDIR=\"$(datadir)/locale\" 	\
	-DXDG_USER_DIRS_UPDATE=\"$(XDG_USER_DIRS_UPDATE)\" \
	$(GTK_CFLAGS)				\
	$(NULL)

EXTRA_DIST =					\
	autogen.sh				\
        intltool-extract.in                     \
        intltool-merge.in                       \
        intltool-update.in                      \
	$(autostart_in_files)			\
	$(gsettingsschema_in_files)		\
	$(NULL)


libraries = $(GTK_LIBS)

bin_PROGRAMS =					\
	xdg-user-dirs-gtk-update		\
	$(NULL)

xdg_user_dirs_gtk_update_SOURCES = parse.c parse.h update.c
xdg_user_dirs_gtk_update_LDADD = $(libraries)

CLEANFILES = 			\
	$(autostart_DATA)	\
	$(gsettings_SCHEMAS)	\
	$(NULL)

DISTCLEANFILES = 				\
	intltool-extract			\
	intltool-merge				\
	intltool-update
