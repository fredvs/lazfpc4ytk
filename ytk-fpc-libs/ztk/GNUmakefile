MAJOR = 2
MINOR = 14
MICRO = 0
LIBZTK_VERSION = $(MAJOR)

I18N_PACKAGE = libztk

CFLAGS = \
	-O1 -g -fPIC -w \
	-I. -Iztk \
    -DHAVE_CONFIG_H \
    -D_LARGEFILE64_SOURCE \
    -D_REENTRANT \
    -DG_LOG_DOMAIN=\"Gdk\" \
    -DATK_COMPILATION \
    -D_FILE_OFFSET_BITS=64 \
    -DG_DISABLE_SINGLE_INCLUDES \
    -DATK_DISABLE_SINGLE_INCLUDES \
    -DG_DISABLE_DEPRECATED \
    -DATK_DISABLE_DEPRECATED \
    -DATK_LOCALEDIR=\"\" \
    $(shell pkg-config --cflags glib-2.0) \
	$(shell pkg-config --cflags gobject-2.0) 

# Libraries for the dynamic linker
LIBS = \
	$(shell pkg-config --libs glib-2.0) \
	$(shell pkg-config --libs gobject-2.0)

ZTK_SOURCES = \
    atk-enum-types.c \
    atkaction.c \
    atkcomponent.c \
    atkdocument.c \
    atkeditabletext.c \
    atkgobjectaccessible.c \
    atkhyperlink.c \
    atkhyperlinkimpl.c \
    atkhypertext.c \
    atkimage.c \
    atkmisc.c \
    atknoopobject.c \
    atknoopobjectfactory.c \
    atkobject.c \
    atkobjectfactory.c \
    atkplug.c \
    atkprivate.c \
    atkrange.c \
    atkregistry.c \
    atkrelation.c \
    atkrelationset.c \
    atkselection.c \
    atksocket.c \
    atkstate.c \
    atkstateset.c \
    atkstreamablecontent.c \
    atktable.c \
    atktablecell.c \
    atktext.c \
    atkutil.c \
    atkvalue.c \
    atkversion.c \
    atkwindow.c 

OBJS = $(ZTK_SOURCES:%.c=%.o)

all: ../libztk.a ../libztk.so

# Static Library
../libztk.a: $(OBJS)
	$(AR) rsc $@ $^

# Dynamic Library
../libztk.so: $(OBJS)
	$(CC) -shared -Wl,-soname,libztk.so.$(MAJOR) -o $@.$(LIBZTK_VERSION) $^ $(LIBS)
	strip ../libztk.so.$(LIBZTK_VERSION)
	cp ../libztk.so.$(LIBZTK_VERSION) ../libztk.so

# Object Compilation
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

.PHONY: clean all
clean:
	rm -f ../libztk.a ../libztk.so ../libztk.so.*
	rm -f $(OBJS)
