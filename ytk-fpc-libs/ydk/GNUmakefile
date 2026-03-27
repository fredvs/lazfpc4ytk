MAJOR = 2
MINOR = 24
MICRO = 23
LIBYDK_VERSION = $(MAJOR)

I18N_PACKAGE = libydk

CFLAGS = \
	-O1 -g -fPIC -w \
	-I. -Iydk -Ix11/ydk -Iydk/x11 -I../ydk-pixbuf \
	-DHAVE_CONFIG_H \
	-D_LARGEFILE64_SOURCE \
	-D_REENTRANT \
	-DG_LOG_DOMAIN=\"Gdk\" \
	-DGDK_COMPILATION \
	-D_FILE_OFFSET_BITS=64 \
	-DGDK_PIXBUF_DISABLE_DEPRECATED \
	-DG_DISABLE_CAST_CHECKS \
	-DG_DISABLE_SINGLE_INCLUDES \
	-DATK_DISABLE_SINGLE_INCLUDES \
	-DGDK_PIXBUF_DISABLE_SINGLE_INCLUDES \
	-DHAVE_XFREE_XINERAMA \
	-DHAVE_UNISTD_H \
    $(shell pkg-config --cflags glib-2.0) \
	$(shell pkg-config --cflags pango) \
	$(shell pkg-config --cflags cairo) \
	$(shell pkg-config --cflags pangocairo) \
	$(shell pkg-config --cflags gio-unix-2.0) \
	$(shell pkg-config --cflags x11) \
	$(shell pkg-config --cflags xext) \
	$(shell pkg-config --cflags xinerama) \
	$(shell pkg-config --cflags randr)

# These are the libraries needed for linking the .so
LIBS = \
	$(shell pkg-config --libs glib-2.0) \
	$(shell pkg-config --libs pango) \
	$(shell pkg-config --libs cairo) \
	$(shell pkg-config --libs pangocairo) \
	$(shell pkg-config --libs gio-unix-2.0) \
	$(shell pkg-config --libs x11) \
	$(shell pkg-config --libs xext) \
	$(shell pkg-config --libs xinerama) \
	$(shell pkg-config --libs randr) \
	-ldl

YDK_SOURCES = \
    gdk.c \
    gdkaliasdef.c \
    gdkapplaunchcontext.c \
    gdkcairo.c \
    gdkcolor.c \
    gdkcursor.c \
    gdkdisplay.c \
    gdkdisplaymanager.c \
    gdkdnd.c \
    gdkdraw.c \
    gdkenumtypes.c \
    gdkevents.c \
    gdkfont.c \
    gdkgc.c \
    gdkglobals.c \
    gdkimage.c \
    gdkkeys.c \
    gdkkeyuni.c \
    gdkmarshalers.c \
    gdkoffscreenwindow.c \
    gdkpango.c \
    gdkpixbuf-drawable.c \
    gdkpixbuf-render.c \
    gdkpixmap.c \
    gdkpolyreg-generic.c \
    gdkrectangle.c \
    gdkregion-generic.c \
    gdkrgb.c \
    gdkscreen.c \
    gdkselection.c \
    gdkvisual.c \
    gdkwindow.c \
    gdkwindowimpl.c 

YDK_X11_SOURCES = \
    x11/gdkapplaunchcontext-x11.c \
    x11/gdkasync.c \
    x11/gdkcolor-x11.c \
    x11/gdkcursor-x11.c \
    x11/gdkdisplay-x11.c \
    x11/gdkdnd-x11.c \
    x11/gdkdrawable-x11.c \
    x11/gdkevents-x11.c \
    x11/gdkfont-x11.c \
    x11/gdkgc-x11.c \
    x11/gdkgeometry-x11.c \
    x11/gdkglobals-x11.c \
    x11/gdkim-x11.c \
    x11/gdkimage-x11.c \
    x11/gdkinput-none.c \
    x11/gdkinput.c \
    x11/gdkkeys-x11.c \
    x11/gdkmain-x11.c \
    x11/gdkpixmap-x11.c \
    x11/gdkproperty-x11.c \
    x11/gdkscreen-x11.c \
    x11/gdkselection-x11.c \
    x11/gdkspawn-x11.c \
    x11/gdkvisual-x11.c \
    x11/gdkwindow-x11.c \
    x11/gdkxftdefaults.c \
    x11/gdkxid.c \
    x11/xsettings-client.c \
    x11/xsettings-common.c 

OBJS = $(YDK_SOURCES:%.c=%.o) $(YDK_X11_SOURCES:%.c=%.o)

all: ../libydk.a ../libydk.so

# Static Library
../libydk.a: $(OBJS)
	$(AR) rsc $@ $^

# Dynamic Library
../libydk.so: $(OBJS)
	$(CC) -shared -Wl,-soname,libydk.so.$(MAJOR) -o $@.$(LIBYDK_VERSION) $^ $(LIBS)
	strip ../libydk.so.$(LIBYDK_VERSION) 
	cp ../libydk.so.$(LIBYDK_VERSION) ../libydk.so

# Object Compilation
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

.PHONY: clean all
clean:
	rm -f ../libydk.a ../libydk.so ../libydk.so.*
	rm -f $(OBJS)
