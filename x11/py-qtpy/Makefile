COMMENT =		provides an abstraction layer of various Qt bindings

MODPY_EGG_VERSION =	2.1.0
DISTNAME =		QtPy-${MODPY_EGG_VERSION}
PKGNAME =		py-qtpy-${MODPY_EGG_VERSION}
CATEGORIES =		x11
REVISION =		1

HOMEPAGE =		https://github.com/spyder-ide/qtpy

# MIT
PERMIT_PACKAGE =	Yes

MODULES =		lang/python

MODPY_PI =		Yes
MODPY_PYBUILD =		setuptools
# XXX fails with PORTS_PRIVSEP
MODPY_PYTEST_ARGS =	qtpy/tests

FLAVORS =		python3
FLAVOR =		python3

TEST_DEPENDS +=		devel/py-mock${MODPY_FLAVOR} \
			x11/py-qt5${MODPY_FLAVOR}

TEST_IS_INTERACTIVE =	x11

.include <bsd.port.mk>
