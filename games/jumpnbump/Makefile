V =		1.61
COMMENT =	game of cute bunnies jumping on each other's heads
DISTNAME =	jumpnbump-${V}
REVISION =	0
CATEGORIES =	games x11

HOMEPAGE =	https://gitlab.com/LibreGames/jumpnbump
MAINTAINER =	Brian Callahan <bcallah@openbsd.org>

# GPLv2+
PERMIT_PACKAGE =	Yes

WANTLIB += SDL2 SDL2_mixer SDL2_net bz2 c m z

MASTER_SITES =	https://gitlab.com/LibreGames/jumpnbump/-/archive/${V}/

BUILD_DEPENDS =	devel/gettext,-tools

LIB_DEPENDS =	archivers/bzip2 \
		devel/sdl2-mixer \
		devel/sdl2-net

RUN_DEPENDS =	devel/desktop-file-utils

USE_GMAKE =	Yes

FAKE_FLAGS =	DESTDIR=

NO_TEST =	Yes

.include <bsd.port.mk>
