COMMENT =		vi-like editor with sam-style structural regex support

V =			0.8
DISTNAME =		vis-${V}
REVISION =		0

TEST_V =		0.5
TEST_DISTNAME =		vis-test-${TEST_V}

CATEGORIES =		editors

HOMEPAGE =		https://github.com/martanne/vis

MAINTAINER =		Klemens Nanni <kn@openbsd.org>

# ISC
PERMIT_PACKAGE =	Yes

WANTLIB += c curses iconv intl m termkey tre ${MODLUA_WANTLIB}

MASTER_SITES =		${HOMEPAGE}/releases/download/v${V}/
MASTER_SITES0 =		${HOMEPAGE}-test/releases/download/v${TEST_V}/

DISTFILES =		${DISTNAME}${EXTRACT_SUFX} \
			${TEST_DISTNAME}${EXTRACT_SUFX}:0

MODULES =		lang/lua
MODLUA_VERSION =	5.3

LIB_DEPENDS =		devel/libtermkey \
			textproc/tre

RUN_DEPENDS =		devel/lpeg,${MODLUA_FLAVOR}>=0.12

TEST_DEPENDS =		editors/vim

CONFIGURE_STYLE =	simple
CONFIGURE_ARGS =	--prefix=${PREFIX} \
			--mandir=${PREFIX}/man

DEBUG_PACKAGES =	${BUILD_PACKAGES}

# for test/core/Makefile
USE_GMAKE =		Yes

post-extract:
	rmdir ${WRKSRC}/test
	mv ${WRKDIR}/${TEST_DISTNAME}/ ${WRKSRC}/test

post-install:
	cd ${PREFIX} && \
		mv bin/vis{,e} && \
		mv man/man1/vis{,e}.1

.include <bsd.port.mk>
