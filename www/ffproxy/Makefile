COMMENT=	filtering HTTP proxy server
DISTNAME=	ffproxy-1.6
REVISION=	3
CATEGORIES=	www
MASTER_SITES=	http://faith.eu.org/ffproxy/

HOMEPAGE=	http://faith.eu.org/programs.html\#ffproxy

# GPLv2+
PERMIT_PACKAGE=	Yes

WANTLIB=		c

CONFIGURE_STYLE=	gnu
CONFIGURE_ARGS=		--datadir=/var

NO_TEST=		Yes

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/ffproxy
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/ffproxy/{db,html}
	${INSTALL_DATA} ${WRKBUILD}/README ${PREFIX}/share/doc/ffproxy
	${INSTALL_DATA} ${WRKBUILD}/sample.config \
		${PREFIX}/share/examples/ffproxy/ffproxy.conf
	${INSTALL_DATA} ${WRKBUILD}/db/* ${PREFIX}/share/examples/ffproxy/db/
	${INSTALL_DATA} ${WRKBUILD}/html/* \
		${PREFIX}/share/examples/ffproxy/html/

.include <bsd.port.mk>
