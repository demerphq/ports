COMMENT =		modernized troff implementation

V =			191015
DISTNAME =		heirloom-doctools-$V
REVISION =		1

CATEGORIES =		textproc print

HOMEPAGE =		https://n-t-roff.github.io/heirloom/doctools.html

MAINTAINER =		Anthony J. Bentley <anthony@anjbe.name>

# see LICENSE and LICENSE.d/
PERMIT_PACKAGE =	Yes

WANTLIB += c m ${COMPILER_LIBCXX}

COMPILER =		base-clang ports-gcc base-gcc

MASTER_SITES =		https://github.com/n-t-roff/heirloom-doctools/releases/download/$V/
EXTRACT_SUFX =		.tar.bz2

FAKE_FLAGS =		ROOT=${DESTDIR}

MAKE_FLAGS =		CC="${CC}" \
			CXX="${CXX}" \
			CCC="${CXX}" \
			CFLAGS="${CFLAGS}" \
			RANLIB=ranlib \
			INSTALL=install \
			STRIP=true \
			BINDIR=${PREFIX}/heirloom-doctools/bin \
			MANDIR=${PREFIX}/heirloom-doctools/man \
			LIBDIR=${PREFIX}/libexec/heirloom-doctools \
			MACDIR=${PREFIX}/share/heirloom-doctools/tmac \
			FNTDIR=${PREFIX}/share/heirloom-doctools/font \
			TABDIR=${PREFIX}/share/heirloom-doctools/nterm \
			HYPDIR=${PREFIX}/share/heirloom-doctools/hyphen \
			PUBDIR=${PREFIX}/share/heirloom-doctools/pub \
			PSTDIR=${PREFIX}/share/heirloom-doctools/font/devpost/postscript \
			REFDIR=${PREFIX}/libexec/heirloom-doctools/reftools \
			EUC=-DEUC

USE_GMAKE =		Yes

NO_TEST =		Yes

MAKE_FILE =		makefile

ALL_TARGET =

.include <bsd.port.mk>
