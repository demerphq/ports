COMMENT =	wsgi request and response object

MODPY_EGG_VERSION = 1.8.7
DISTNAME =	WebOb-${MODPY_EGG_VERSION}
PKGNAME =	py-${DISTNAME:L}
REVISION =	2

CATEGORIES =	www devel

HOMEPAGE =	https://webob.org/

# MIT
PERMIT_PACKAGE =	Yes

MODULES =	lang/python

MODPY_PI =	Yes
MODPY_PYBUILD =	setuptools

FLAVORS =	python3
FLAVOR =	python3

DOCS =		differences.txt do-it-yourself.txt index.txt whatsnew-*.txt \
		reference.txt
EXAMPLES =	comment-example.txt file-example.txt jsonrpc-example.txt \
		wiki-example.txt

TEST_DEPENDS =	www/py-webtest${MODPY_FLAVOR}
TEST_ENV +=	PYTHONPATH=${WRKSRC}/lib

post-extract:
	find ${WRKSRC} -perm 0666 -exec chmod 0644 {} +

PYPKGNAME =	${MODPY_PY_PREFIX}webob

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/${PYPKGNAME}
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/${PYPKGNAME}
	cd ${WRKSRC}/docs && ${INSTALL_DATA} ${DOCS} \
	    ${PREFIX}/share/doc/${PYPKGNAME}
	cd ${WRKSRC}/docs && ${INSTALL_DATA} ${EXAMPLES} \
	    ${PREFIX}/share/examples/${PYPKGNAME}

.include <bsd.port.mk>
