COMMENT =		library for property based testing

# newer versions required new dep 'exceptiongroup'
MODPY_EGG_VERSION =	6.47.1
DISTNAME =		hypothesis-${MODPY_EGG_VERSION}
PKGNAME =		py-hypothesis-${MODPY_EGG_VERSION}
CATEGORIES =		devel
REVISION =		0

HOMEPAGE =		https://hypothesis.works/

# MPL 2.0
PERMIT_PACKAGE =	Yes

MODULES =		lang/python

MODPY_PI =		Yes
MODPY_PYBUILD =		setuptools

FLAVORS =		python3
FLAVOR =		python3

RUN_DEPENDS =		devel/py-attrs${MODPY_FLAVOR} \
			devel/py-coverage${MODPY_FLAVOR} \
			devel/py-sortedcontainers${MODPY_FLAVOR}

# Primary author is completely uninterested in supplying tests via PyPI
NO_TEST =		Yes

.include <bsd.port.mk>
