ONLY_FOR_ARCHS= ${APM_ARCHS}

COMMENT=	light-weight system monitor

# there's a start of an attempt to update to a recent version in openbsd-wip
GH_ACCOUNT=	brndnmtthws
GH_PROJECT=	conky
GH_TAGNAME=	1.9.0
REVISION=	22

# remove after updating:
DISTFILES=	conky_0-{}${GH_TAGNAME}.tar.gz

CATEGORIES=	sysutils

# mostly GPLv3; see COPYING
PERMIT_PACKAGE=	Yes

WANTLIB=	c crypto curl curses glib-2.0 iconv intl kvm lzma m \
		nghttp2 ossaudio pcre2-8 pthread ssl xml2 z ${MODLUA_WANTLIB}

MODULES=	lang/lua
MODLUA_SA=	Yes

LIB_DEPENDS=	devel/glib2 \
		net/curl \
		textproc/libxml \
		${MODLUA_LIB_DEPENDS}

FLAVORS=	no_x11 xmms2
FLAVOR?=

CONFIGURE_STYLE= autoreconf
AUTOCONF_VERSION= 2.69
AUTOMAKE_VERSION= 1.16
BUILD_DEPENDS=	textproc/docbook2x \
		textproc/docbook-xsl
AUTORECONF=	${WRKSRC}/autogen.sh

CONFIGURE_ARGS=	--enable-mpd \
		--enable-rss \
		--disable-config-output \
		--disable-moc \
		--disable-portmon \
		--enable-lua \
		--enable-curl \
		--with-libiconv-prefix="${LOCALBASE}"
CONFIGURE_ENV=	CPPFLAGS="-I${LOCALBASE}/include" LDFLAGS="-L${LOCALBASE}/lib" \
		LUA_CFLAGS="`pkg-config --cflags ${MODLUA_DEP}`" \
		LUA_LIBS="`pkg-config --libs ${MODLUA_DEP}`"

.if ${FLAVOR:Mno_x11}
.  if ${FLAVOR:Mxmms2}
ERRORS+="Fatal: nonsense combination of flavors"
.  else
CONFIGURE_ARGS+=--disable-double-buffer \
		--disable-own-window \
		--disable-xdamage \
		--disable-xft \
		--disable-x11
.  endif
.else
CONFIGURE_ARGS+=--enable-imlib2
LIB_DEPENDS+=	graphics/imlib2
WANTLIB += Imlib2 X11 Xdamage Xext Xfixes Xft
WANTLIB += Xrender expat fontconfig freetype xcb
.endif

.if ${FLAVOR:Mxmms2}
CONFIGURE_ARGS+=--enable-xmms2
LIB_DEPENDS+=	audio/xmms2
WANTLIB+=	xmmsclient
.endif

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/conky
	${INSTALL_DATA} ${WRKSRC}/doc/*.html ${PREFIX}/share/doc/conky
	${INSTALL_DATA} ${WRKSRC}/README ${PREFIX}/share/doc/conky

FAKE_FLAGS=	configdir=${PREFIX}/share/examples/conky

.include <bsd.port.mk>
