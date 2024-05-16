ACLOCAL_AMFLAGS := -I m4


AM_CFLAGS := -Wundef \
        -Wstrict-prototypes \
        -Wno-trigraphs \
        -g -O0 \
        $(LOCBASEUTIL_CFLAGS) \
        -fno-inline \
        -fno-short-enums \
        -fpic \
        -D_GNU_SOURCE \
        -DHAVE_CONFIG_H=1 \
        -DBUILD_DIVSUFSORT64

AM_CPPFLAGS := \
        -I. \
        -I$(WORKSPACE)/OTA/streaming/external/libchrome \
        -I$(WORKSPACE)/OTA/streaming/frameworks/native/libs/binder/include \
        -I$(WORKSPACE)/OTA/streaming/external/libbrillo \
        -I$(WORKSPACE)/OTA/streaming/external/modp_b64 \
        -I$(WORKSPACE)/system/core/base/include \
        -I$(WORKSPACE)/system/core/include \
        -I$(WORKSPACE)/OTA/system/core/libbinderwrapper/include \
        -I$(WORKSPACE)/security/commonsys-intf/securemsm/mdtp/third_party/openssl/include \
        -D_FILE_OFFSET_BITS=64 \
        -D_USE_RTTI_FOR_TYPE_TAGS \
        -std=c++11 \
        -USE_GLIB

AUTOMAKE_OPTIONS = subdir-objects

AM_LDFLAGS := -shared -version-info 1:0:0

cpp_SOURCES :=  binder_wrapper.cc \
                real_binder_wrapper.cc

lib_LTLIBRARIES := libbinderwrapper.la
libbinderwrapper_la_SOURCES := $(cpp_SOURCES)

if USE_GLIB
libbinderwrapper_la_CFLAGS := $(AM_CFLAGS) -DUSE_GLIB @GLIB_CFLAGS@
libbinderwrapper_la_CPPFLAGS := $(AM_CPPFLAGS) -fpermissive -DUSE_GLIB @GLIB_CFLAGS@
libbinderwrapper_la_LIBADD := -lm -lssl -lcrypto -lbrillo -lchrome -lpthread -lbinderstreaming @GLIB_LIBS@
libbinderwrapper_la_LDFLAGS = -shared
else
libbinderwrapper_la_CFLAGS := $(AM_CFLAGS)
libbinderwrapper_la_CPPFLAGS := $(AM_CPPFLAGS) -fpermissive
libbinderwrapper_la_LIBADD := -lm -lssl -lcrypto -lbrillo -lchrome -lpthread -lbinderstreaming
libbinderwrapper_la_LDFLAGS = -shared
endif

