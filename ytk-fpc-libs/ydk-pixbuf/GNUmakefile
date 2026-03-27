MAJOR = 2
MINOR = 31
MICRO = 1
LIBYDKPIXBUF_VERSION = $(MAJOR)

I18N_PACKAGE = libydk-pixbuf

# Added -fPIC here (which you already had) is essential for .so
CFLAGS = \
	-O1 -g -fPIC -w \
	-I. -Iydk-pixbuf \
    -D_LARGEFILE64_SOURCE \
    -D_REENTRANT \
    -DG_LOG_DOMAIN=\"GdkPixbuf\" \
    -DDGDK_PIXBUF_COMPILATION \
    -D_FILE_OFFSET_BITS=64 \
    -DGDK_PIXBUF_ENABLE_BACKEND \
    -DG_DISABLE_SINGLE_INCLUDES \
    -D_POSIX_C_SOURCE=200809L \
    -DINCLUDE_png \
    -DINCLUDE_xbm \
    -DINCLUDE_xpm \
    -DPACKAGE="$(I18N_PACKAGE)" \
    -DGDK_PIXBUF_LOCALEDIR=\"\" \
    -DHAVE_UNISTD_H \
	$(shell pkg-config --cflags glib-2.0) \
	$(shell pkg-config --cflags gio-2.0) \
	$(shell pkg-config --cflags gobject-2.0) \
	$(shell pkg-config --cflags libpng) 

LIBS = \
	$(shell pkg-config --libs glib-2.0) \
	$(shell pkg-config --libs gio-2.0) \
	$(shell pkg-config --libs gobject-2.0) \
	$(shell pkg-config --libs libpng)

YDK_PIXBUF_SOURCES = \
    gdk-pixbuf-animation.c \
    gdk-pixbuf-data.c \
    gdk-pixbuf-enum-types.c \
    gdk-pixbuf-io.c \
    gdk-pixbuf-loader.c \
    gdk-pixbuf-scale.c \
    gdk-pixbuf-scaled-anim.c \
    gdk-pixbuf-simple-anim.c \
    gdk-pixbuf-util.c \
    gdk-pixbuf.c \
    gdk-pixdata.c \
    io-pixdata.c \
    io-png.c \
    io-xbm.c \
    io-xpm.c \
    pixops/pixops.c 

OBJS = $(YDK_PIXBUF_SOURCES:%.c=%.o)

# Target for both
all: ../libydk-pixbuf.a ../libydk-pixbuf.so

# Static Library
../libydk-pixbuf.a: $(OBJS)
	$(AR) rsc $@ $^

# Dynamic Library (Shared Object)
../libydk-pixbuf.so: $(OBJS)
	$(CC) -shared -Wl,-soname,libydk-pixbuf.so.$(MAJOR) -o $@.$(LIBYDKPIXBUF_VERSION) $^ $(LIBS)
	strip ../libydk-pixbuf.so.$(LIBYDKPIXBUF_VERSION)
	cp ../libydk-pixbuf.so.$(LIBYDKPIXBUF_VERSION) ../libydk-pixbuf.so

# Object Compilation
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

.PHONY: clean all
clean:
	rm -f ../libydk-pixbuf.a ../libydk-pixbuf.so ../libydk-pixbuf.so.*
	rm -f $(OBJS)
