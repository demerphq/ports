COMMENT =		c++ commandline flags processing library

GH_ACCOUNT =		gflags
GH_PROJECT =		gflags
GH_TAGNAME =		v2.2.2
REVISION =		0

SHARED_LIBS +=		gflags               1.0      # .0.0
SHARED_LIBS +=		gflags_nothreads     1.0      # .0.0

CATEGORIES =		devel

HOMEPAGE =		https://gflags.github.io/gflags/

# New BSD
PERMIT_PACKAGE =	Yes

WANTLIB += ${COMPILER_LIBCXX} m

COMPILER =		base-clang ports-gcc base-gcc

MODULES =		devel/cmake

CONFIGURE_ARGS +=	-DBUILD_SHARED_LIBS=ON \
			-DBUILD_STATIC_LIBS=ON \
			-DBUILD_TESTING=ON

# evertyhing except tests
ALL_TARGET =		${SHARED_LIBS:Mgflags*}

do-build:
	@${MODCMAKE_BUILD_TARGET} -t ${ALL_TARGET}

# build whatever is left (ca. 11 C++ test files)
pre-test:
	@${MODCMAKE_BUILD_TARGET}

.include <bsd.port.mk>
