COMMENT =		Chinese truetype font derived from Klee One

V =			0.943
PKGNAME =		zh-iansui-${V}

GH_ACCOUNT =		ButTaiwan
GH_PROJECT =		iansui
GH_TAGNAME =		v${V}

CATEGORIES =		fonts chinese x11

HOMEPAGE =		https://github.com/ButTaiwan/iansui

MAINTAINER =		Kevin Lo <kevlo@openbsd.org>

# SIL OFL 1.1
PERMIT_PACKAGE =	Yes

NO_BUILD =		Yes
NO_TEST =		Yes

FONTDIR =		${PREFIX}/share/fonts/iansui

do-install:
	${INSTALL_DATA_DIR} ${FONTDIR}
	${INSTALL_DATA} ${WRKSRC}/Iansui${V:S/.//:C/.$//}-Regular.ttf \
		${FONTDIR}/Iansui-Regular.ttf

.include <bsd.port.mk>
