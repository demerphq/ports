COMMENT =	help visualize profiling data collected with the cProfile

MODPY_EGG_VERSION = 1.4.5
DISTNAME =	pyprof2calltree-${MODPY_EGG_VERSION}
PKGNAME =	py-${DISTNAME}
REVISION =	5

CATEGORIES =	devel

HOMEPAGE =	https://github.com/pwaller/pyprof2calltree

# BSD-derived
PERMIT_PACKAGE =	Yes

MODPY_PI =	Yes

MODULES =	lang/python

MODPY_PYBUILD =		setuptools

FLAVORS =	python3
FLAVOR =	python3

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/${MODPY_PY_PREFIX}pyprof2calltree
	${INSTALL_DATA} ${WRKSRC}/README.rst \
		${PREFIX}/share/doc/${MODPY_PY_PREFIX}pyprof2calltree

.include <bsd.port.mk>
