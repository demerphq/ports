COMMENT =		c protocol buffers

V =			1.4.1
DISTNAME =		protobuf-c-$V

SHARED_LIBS =		protobuf-c 2.0	# 1.0

CATEGORIES =		devel

HOMEPAGE =		https://github.com/protobuf-c/protobuf-c/wiki

MASTER_SITES=		https://github.com/protobuf-c/protobuf-c/releases/download/v$V/

# New BSD
PERMIT_PACKAGE =	Yes

WANTLIB =		c m protobuf protoc pthread ${COMPILER_LIBCXX} z

COMPILER =		base-clang ports-gcc
CXXFLAGS +=		-std=gnu++11

LIB_DEPENDS =		devel/protobuf

CONFIGURE_STYLE =	gnu

CONFIGURE_ENV =		CPPFLAGS="-I${LOCALBASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib"

USE_GMAKE =		Yes

SEPARATE_BUILD =	Yes

pre-configure:
	sed -i -E 's,(--plugin|--cpp_out),-I${LOCALBASE}/include &,' ${WRKSRC}/Makefile.in

.include <bsd.port.mk>
