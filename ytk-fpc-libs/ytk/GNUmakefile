MAJOR = 2
MINOR = 24
MICRO = 23
LIBYTK_VERSION = $(MAJOR)

I18N_PACKAGE = libytk
BLD_PREFIX = "/usr/local"
BLD_SYSCONFDIR = "/usr/local/etc"
BLD_DATADIR = "/usr/local/share"
BLD_LIBDIR = "/usr/local/lib"

CFLAGS = \
	-O1 -g -fPIC -w \
	-I. -Iytk -I../ydk -I../ydk/ydk -I../ydk/x11 -I../ydk-pixbuf -I../ztk \
    -DHAVE_CONFIG_H \
    -D_LARGEFILE64_SOURCE \
    -D_REENTRANT \
    -DG_LOG_DOMAIN=\"Gtk\" \
    -DGTK_COMPILATION \
    -D_FILE_OFFSET_BITS=64 \
    -DG_DISABLE_CAST_CHECKS \
    -DG_DISABLE_SINGLE_INCLUDES \
    -DDATK_DISABLE_SINGLE_INCLUDES \
    -DGDK_PIXBUF_DISABLE_SINGLE_INCLUDES \
    -DGTK_DISABLE_SINGLE_INCLUDES \
    -DGDK_PIXBUF_DISABLE_DEPRECATED \
    -DGTK_DISABLE_DEPRECATED \
    -DGTK_PRINT_BACKENDS=\"file,lpr\" \
    -DGTK_PRINT_BACKEND_ENABLE_UNSUPPORTED \
    -DGTK_PRINT_PREVIEW_COMMAND=\"\" \
    -D_POSIX_C_SOURCE=200809L \
    -DGTK_VERSION=\"2.24.23\" \
    -DGTK_BINARY_VERSION=\"2.10.0\" \
    -DGTK_HOST=\"ardour\" \
    -DPACKAGE="$(I18N_PACKAGE)" \
    -DGETTEXT_PACKAGE=\"$(I18N_PACKAGE)\" \
    -DGTK_DATA_PREFIX=\"$(BLD_PREFIX)\" \
    -DGTK_SYSCONFDIR=\"$(BLD_SYSCONFDIR)\" \
    -DGTK_DATA_DIR=\"$(BLD_DATADIR)\" \
    -DGTK_LIBDIR=\"$(BLD_LIBDIR)\" \
    -DHAVE_UNISTD_H \
    $(shell pkg-config --cflags glib-2.0) \
	$(shell pkg-config --cflags pango) \
	$(shell pkg-config --cflags cairo) \
	$(shell pkg-config --cflags pangocairo) \
	$(shell pkg-config --cflags gmodule-2.0) \
	$(shell pkg-config --cflags x11) \
	$(shell pkg-config --cflags xext) 

# Libraries for the dynamic linker
LIBS = \
	$(shell pkg-config --libs glib-2.0) \
	$(shell pkg-config --libs pango) \
	$(shell pkg-config --libs cairo) \
	$(shell pkg-config --libs pangocairo) \
	$(shell pkg-config --libs gmodule-2.0) \
	$(shell pkg-config --libs x11) \
	$(shell pkg-config --libs xext) \
	-lm

YTK_SOURCES = \
    fnmatch.c gtkaboutdialog.c gtkaccelgroup.c gtkaccellabel.c gtkaccelmap.c \
    gtkaccessible.c gtkaction.c gtkactiongroup.c gtkactivatable.c gtkadjustment.c \
    gtkaliasdef.c gtkalignment.c gtkarrow.c gtkaspectframe.c gtkassistant.c \
    gtkbbox.c gtkbin.c gtkbindings.c gtkbox.c gtkbuildable.c gtkbuilder.c \
    gtkbuilderparser.c gtkbutton.c gtkcelleditable.c gtkcelllayout.c \
    gtkcellrenderer.c gtkcellrendereraccel.c gtkcellrenderercombo.c \
    gtkcellrendererpixbuf.c gtkcellrendererprogress.c gtkcellrendererspin.c \
    gtkcellrendererspinner.c gtkcellrenderertext.c gtkcellrenderertoggle.c \
    gtkcellview.c gtkcheckbutton.c gtkcheckmenuitem.c gtkcolorbutton.c \
    gtkcolorsel.c gtkcolorseldialog.c gtkcombobox.c gtkcomboboxentry.c \
    gtkcomboboxtext.c gtkcontainer.c gtkdialog.c gtkdrawingarea.c \
    gtkeditable.c gtkentry.c gtkentrybuffer.c gtkentrycompletion.c \
    gtkeventbox.c gtkexpander.c gtkfilechooser.c gtkfilechooserbutton.c \
    gtkfilechooserdefault.c gtkfilechooserdialog.c gtkfilechooserembed.c \
    gtkfilechooserentry.c gtkfilechoosersettings.c gtkfilechooserutils.c \
    gtkfilechooserwidget.c gtkfilefilter.c gtkfilesystem.c gtkfilesystemmodel.c \
    gtkfixed.c gtkfontbutton.c gtkfontsel.c gtkframe.c gtkgc.c \
    gtkhandlebox.c gtkhbbox.c gtkhbox.c gtkhpaned.c gtkhruler.c \
    gtkhscale.c gtkhscrollbar.c gtkhseparator.c gtkhsv.c gtkiconcache.c \
    gtkiconcachevalidator.c gtkiconfactory.c gtkicontheme.c gtkiconview.c \
    gtkimage.c gtkimagemenuitem.c gtkimcontext.c gtkimcontextsimple.c \
    gtkimmodule.c gtkimmulticontext.c gtkinfobar.c gtkinvisible.c \
    gtkitem.c gtkkeyhash.c gtklabel.c gtklayout.c gtklinkbutton.c \
    gtkliststore.c gtkmain.c gtkmarshal.c gtkmarshalers.c gtkmenu.c \
    gtkmenubar.c gtkmenuitem.c gtkmenushell.c gtkmenutoolbutton.c \
    gtkmessagedialog.c gtkmisc.c gtkmnemonichash.c gtkmodules.c \
    gtkmountoperation.c gtknotebook.c gtkobject.c gtkoffscreenwindow.c \
    gtkoptionmenu.c gtkorientable.c gtkpaned.c gtkpango.c gtkpathbar.c \
    gtkplug.c gtkprogress.c gtkprogressbar.c gtkquery.c gtkradioaction.c \
    gtkradiobutton.c gtkradiomenuitem.c gtkradiotoolbutton.c gtkrange.c \
    gtkrbtree.c gtkrc.c gtkrecentaction.c gtkrecentchooser.c \
    gtkrecentchooserdefault.c gtkrecentchooserdialog.c gtkrecentchoosermenu.c \
    gtkrecentchooserutils.c gtkrecentchooserwidget.c gtkrecentfilter.c \
    gtkrecentmanager.c gtkruler.c gtkscale.c gtkscalebutton.c \
    gtkscrollbar.c gtkscrolledwindow.c gtksearchengine.c gtksearchenginesimple.c \
    gtkselection.c gtkseparator.c gtkseparatormenuitem.c gtkseparatortoolitem.c \
    gtksettings.c gtkshow.c gtksizegroup.c gtksocket.c gtkspinbutton.c \
    gtkspinner.c gtkstatusbar.c gtkstock.c gtkstyle.c gtktable.c \
    gtktearoffmenuitem.c gtktextbtree.c gtktextbuffer.c gtktextbufferrichtext.c \
    gtktextbufferserialize.c gtktextchild.c gtktextdisplay.c gtktextiter.c \
    gtktextlayout.c gtktextmark.c gtktextsegment.c gtktexttag.c \
    gtktexttagtable.c gtktexttypes.c gtktextutil.c gtktextview.c \
    gtkthemes.c gtktoggleaction.c gtktogglebutton.c gtktoggletoolbutton.c \
    gtktoolbar.c gtktoolbutton.c gtktoolitem.c gtktoolitemgroup.c \
    gtktoolpalette.c gtktoolshell.c gtktooltip.c gtktooltips.c \
    gtktreedatalist.c gtktreednd.c gtktreemodel.c gtktreemodelfilter.c \
    gtktreemodelsort.c gtktreeselection.c gtktreesortable.c gtktreestore.c \
    gtktreeview.c gtktreeviewcolumn.c gtktypebuiltins.c gtktypeutils.c \
    gtkuimanager.c gtkvbbox.c gtkvbox.c gtkviewport.c gtkvpaned.c \
    gtkvruler.c gtkvscale.c gtkvscrollbar.c gtkvseparator.c gtkwidget.c \
    gtkwindow-decorate.c gtkwindow.c 

YTK_X11_SOURCES = \
    gtkclipboard.c gtkdnd.c gtkmountoperation-x11.c \
    gtkplug-x11.c gtksocket-x11.c gtkxembed.c 

OBJS = $(YTK_SOURCES:%.c=%.o) $(YTK_X11_SOURCES:%.c=%.o)

all: ../libytk.a ../libytk.so

# Static Library
../libytk.a: $(OBJS)
	$(AR) rsc $@ $^

# Dynamic Library
../libytk.so: $(OBJS)
	$(CC) -shared -Wl,-soname,libytk.so.$(MAJOR) -o $@.$(LIBYTK_VERSION) $^ $(LIBS)
	strip ../libytk.so.$(LIBYTK_VERSION)
	cp ../libytk.so.$(LIBYTK_VERSION) ../libytk.so

# Object Compilation
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

.PHONY: clean all
clean:clean
	rm -f ../libytk.a ../libytk.so ../libytk.so.*
	rm -f $(OBJS)
