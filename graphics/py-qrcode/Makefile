COMMENT =		QR Code image generator

MODPY_EGG_VERSION =	7.3.1
DISTNAME =		qrcode-${MODPY_EGG_VERSION}
PKGNAME =		py-${DISTNAME}
REVISION =		2

CATEGORIES =		graphics textproc

MAINTAINER =		Ingo Feinerer <feinerer@logic.at>

# BSD
PERMIT_PACKAGE =	Yes

MODULES =		lang/python
MODPY_PI =		Yes
MODPY_PYBUILD =		setuptools
MODPY_PYTEST_ARGS =	qrcode

RUN_DEPENDS =		devel/py-six${MODPY_FLAVOR} \
			graphics/py-Pillow${MODPY_FLAVOR}
TEST_DEPENDS =		devel/py-mock${MODPY_FLAVOR} \
			devel/py-test-cov${MODPY_FLAVOR}

FLAVORS =		python3
FLAVOR =		python3

.include <bsd.port.mk>
