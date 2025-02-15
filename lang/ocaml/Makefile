COMMENT =	   ML language with complete class-based objective system

# XXX Don't even think of updating ocaml alone.
# Do check that the ports that depend on it still work, or repair them.
VERSION=		4.12.1
REVISION=		2

PKGNAME =		ocaml-${VERSION:C/\+//}

# OCaml has no binary compatibility between releases.
PKGSPEC =	ocaml-=${VERSION:C/\+//}

CATEGORIES=	lang
BASENAME =	${DISTNAME:R}
MASTER_SITES=	https://caml.inria.fr/pub/distrib/${BASENAME}/
DOCFILES=	${BASENAME}-refman-html.tar.gz
DISTFILES=	${DISTNAME}.tar.gz ${DOCFILES}
DISTNAME =	ocaml-${VERSION}

HOMEPAGE=	https://ocaml.org/
MAINTAINER=	Anil Madhavapeddy <avsm@openbsd.org>

# QPL/LGPL
PERMIT_PACKAGE=	Yes

.include <bsd.port.arch.mk>

AUTOCONF_VERSION =	2.69
CONFIGURE_STYLE =	gnu autoconf no-autoheader
CONFIGURE_ENV+=		CFLAGS="${CFLAGS}" \
			CPPFLAGS="${CFLAGS} ${CPPFLAGS}" \
			LDFLAGS="${LDFLAGS}"
.if ${PROPERTIES:Mclang}
CONFIGURE_ENV+=		OBJDUMP=/usr/bin/llvm-objdump
.endif
CONFIGURE_ARGS +=	--disable-force-safe-string \
			--enable-ocamltest

CFLAGS +=	-I${LOCALBASE}/include
LDFLAGS +=	-L${LOCALBASE}/lib

# non-PIC assembly in asmrun/i386.S
.if ${MACHINE_ARCH} == "i386"
LDFLAGS+=		-Wl,-z,notext
.endif

USE_GMAKE=	Yes

WANTLIB =		c iberty m pthread z

# for libbfd (used by ocamlobjinfo on .cmxs files)
BUILD_DEPENDS +=	devel/gdb

.if ${PROPERTIES:Mocaml_native}
ALL_TARGET=	world.opt
PKG_ARGS +=	-Dnative=1

.if ${PROPERTIES:Mocaml_native_dynlink}
PKG_ARGS +=	-Ddynlink=1
.else
PKG_ARGS +=	-Ddynlink=0
.endif

.else
ALL_TARGET=	world
PKG_ARGS +=	-Dnative=0
NO_TEST   =	yes
.endif

TEST_TARGET =	tests

DPB_PROPERTIES +=	parallel

post-install:
	@${INSTALL_DATA_DIR} ${PREFIX}/share/doc/ocaml/html/libref
	@${INSTALL_DATA} ${WRKDIR}/htmlman/*.{html,gif,css} \
		${PREFIX}/share/doc/ocaml/html
	@${INSTALL_DATA} ${WRKDIR}/htmlman/libref/* \
		${PREFIX}/share/doc/ocaml/html/libref
	@${INSTALL_DATA} \
		${WRKSRC}/{LICENSE,Changes} \
		${PREFIX}/share/doc/ocaml

# PFRAG.native was generated from PLIST with:
# egrep '(ocamlopt|\.cmx|\.cmxa|\.cmxs|\.opt|opt\.1|opt.cmi|\.native|\.o)$'

# One test in the suite (testsocket.ml) requires an active
# connection to internet
TEST_IS_INTERACTIVE =		Yes


.include <bsd.port.mk>
