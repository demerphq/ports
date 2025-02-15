COMMENT =	desktop client for Matrix using Qt and C++17

GH_ACCOUNT =	Nheko-Reborn
GH_PROJECT =	nheko
GH_TAGNAME =	v0.10.2

CATEGORIES=	net

# GPLv3
PERMIT_PACKAGE=	Yes

WANTLIB += ${COMPILER_LIBCXX} Qt5Concurrent Qt5Core Qt5DBus Qt5Gui
WANTLIB += Qt5Multimedia Qt5Network Qt5Qml Qt5QmlModels Qt5Quick
WANTLIB += Qt5QuickControls2 Qt5QuickWidgets Qt5Svg Qt5Widgets
WANTLIB += c cmark coeurl crypto glib-2.0 gobject-2.0 gstbase-1.0
WANTLIB += gstreamer-1.0 gstsdp-1.0 gstwebrtc-1.0 intl lmdb m
WANTLIB += matrix_client olm qt5keychain spdlog ssl xcb xcb-ewmh

MODULES =	devel/cmake \
		x11/qt5

# C++17
COMPILER =	base-clang ports-gcc

RUN_DEPENDS =	devel/desktop-file-utils \
		x11/qt5/qtgraphicaleffects \
		x11/gtk+3,-guic

BUILD_DEPENDS = databases/lmdbxx \
		devel/boost \
		textproc/asciidoc \
		textproc/nlohmann-json \
		x11/qt5/qtbase

LIB_DEPENDS =	databases/lmdb \
		devel/coeurl \
		devel/mtxclient \
		devel/olm \
		devel/spdlog \
		multimedia/gstreamer1/core \
		multimedia/gstreamer1/plugins-base \
		security/qtkeychain \
		textproc/cmark \
		x11/qt5/qtmultimedia \
		x11/qt5/qtquickcontrols2 \
		x11/qt5/qtsvg

.include <bsd.port.mk>
