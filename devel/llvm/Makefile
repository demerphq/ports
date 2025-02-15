# XXX If broken on an architecture, remove the arch from LLVM_ARCHS.
ONLY_FOR_ARCHS = ${LLVM_ARCHS}

DPB_PROPERTIES = parallel

COMMENT-main =	modular, fast C/C++/ObjC compiler, static analyzer and tools
COMMENT-lldb =	LLDB debugger
COMMENT-python =	Python bindings for Clang

# XXX: Remember to bump MODCLANG_VERSION in lang/clang/clang.port.mk when
# updating this port.
LLVM_V =	13.0.0
DISTNAME =	llvm-${LLVM_V}.src
PKGNAME =	llvm-${LLVM_V}
PKGSPEC-main =	llvm-=${LLVM_V}
PKGNAME-python =	py3-llvm-${LLVM_V}
PKGNAME-lldb =	lldb-${LLVM_V}
REVISION-main =	4
REVISION-lldb =	1
REVISION-python = 0

CATEGORIES =	devel

SHARED_LIBS =	clang		8.2 \
		clang-cpp	1.0 \
		lldb		3.0 \
		LTO		6.1 \
		Remarks		0.0

# packager notes in http://llvm.org/docs/Packaging.html
HOMEPAGE =	https://www.llvm.org/

MAINTAINER=	Jeremie Courreges-Anglas <jca@wxcvbn.org>

# In transition from BSD-ish to Apache 2 + LLVM exceptions
PERMIT_PACKAGE =	Yes

MASTER_SITES =	https://github.com/llvm/llvm-project/releases/download/llvmorg-${LLVM_V}/
EXTRACT_SUFX =	.tar.xz
DISTFILES =	llvm-${LLVM_V}.src${EXTRACT_SUFX} \
		clang-${LLVM_V}.src${EXTRACT_SUFX} \
		lld-${LLVM_V}.src${EXTRACT_SUFX} \
		lldb-${LLVM_V}.src${EXTRACT_SUFX}

MULTI_PACKAGES = -main -python -lldb

COMPILER =		base-clang ports-gcc
MODULES =		devel/cmake \
			lang/python

MODPY_ADJ_FILES =	tools/clang/tools/clang-format/git-clang-format \
			tools/clang/tools/scan-view/bin/scan-view \
			tools/clang/utils/hmaptool/hmaptool \
			tools/clang/tools/scan-build-py/bin/* \
			tools/clang/tools/scan-build-py/libexec/*

TEST_DEPENDS =		devel/dejagnu \
			shells/bash
BUILD_DEPENDS +=	devel/swig \
			textproc/py-sphinx${MODPY_FLAVOR} \
			textproc/py-recommonmark${MODPY_FLAVOR}

.include <bsd.port.arch.mk>

.if !${PROPERTIES:Mclang}
RUN_DEPENDS +=		lang/gcc/${MODGCC4_VERSION},-c++
.endif

WANTLIB =		${COMPILER_LIBCXX} c edit m pthread

WANTLIB-main =		${WANTLIB} z
LIB_DEPENDS-main =	${LIB_DEPENDS}

# clang python module loads libclang.so dynamically with cdll.LoadLibrary()
WANTLIB-python =	clang
RUN_DEPENDS-python =	${MODPY_RUN_DEPENDS}
LIB_DEPENDS-python =	${BUILD_PKGPATH},-main

WANTLIB-lldb =		${WANTLIB} ${MODPY_WANTLIB}
WANTLIB-lldb +=		clang-cpp curses edit form panel
RUN_DEPENDS-lldb =	${MODPY_RUN_DEPENDS} \
			devel/py-six${MODPY_FLAVOR}
LIB_DEPENDS-lldb =	${LIB_DEPENDS} \
			${BUILD_PKGPATH},-main

CONFIGURE_STYLE =	cmake
CONFIGURE_ARGS =	-DLLVM_ENABLE_FFI:Bool=False \
			-DLLVM_ENABLE_TERMINFO:Bool=False \
			-DLLVM_ENABLE_RTTI:Bool=True \
			-DCMAKE_DISABLE_FIND_PACKAGE_LibXml2:Bool=True \
			-DLLVM_LINK_LLVM_DYLIB:Bool=True \
			-DLLVM_BUILD_LLVM_DYLIB:Bool=True \
			-DGO_EXECUTABLE=GO_EXECUTABLE-NOTFOUND \
			-DCMAKE_DISABLE_FIND_PACKAGE_Backtrace:Bool=True \
			-DLLDB_USE_SYSTEM_SIX=ON \
			-DLLDB_ENABLE_LZMA=OFF \
			-DLLDB_ENABLE_LUA=OFF \
			-DLLDB_ENABLE_LIBXML2=OFF

# Disable some protections in the compiler to regain performance.
.if ${MACHINE_ARCH} == "aarch64" || ${MACHINE_ARCH} == "amd64" || \
    ${MACHINE_ARCH} == "i386" || ${MACHINE_ARCH} == "mips64" || \
    ${MACHINE_ARCH} == "mips64el" || ${MACHINE_ARCH} == "powerpc"
CXXFLAGS+=	-fno-ret-protector
.endif
.if ${MACHINE_ARCH} == "amd64" || ${MACHINE_ARCH} == "i386"
CXXFLAGS+=	-mno-retpoline
.endif

# Omit frame pointer to improve performance.
.if ${MACHINE_ARCH} == "mips64" || ${MACHINE_ARCH} == "mips64el"
CXXFLAGS+=	-fomit-frame-pointer
.endif

TEST_TARGET =		check check-clang

# XXX sync
GCC_VER =		8.4.0
.if ${MACHINE_ARCH} == "amd64"
GCC_CONFIG =		x86_64-unknown-openbsd${OSREV}
.else
GCC_CONFIG =		${MACHINE_ARCH}-unknown-openbsd${OSREV}
.endif
CLANG_INCLUDE_PATH =	lib/clang/${LLVM_V}/include
SUBST_VARS +=		CLANG_INCLUDE_PATH LLVM_V GCC_VER GCC_CONFIG

# hack to disable the use of -Bsymbolic-functions
.if ${PROPERTIES:Mlld}
OPENBSD_LD_IS_LLD =	TRUE
.else
OPENBSD_LD_IS_LLD =	FALSE
.endif
SUBST_VARS +=		OPENBSD_LD_IS_LLD

post-extract:
	mv ${WRKDIR}/clang-${LLVM_V}.src ${WRKSRC}/tools/clang
	mv ${WRKDIR}/lld-${LLVM_V}.src ${WRKSRC}/tools/lld
	mv ${WRKDIR}/lldb-${LLVM_V}.src ${WRKSRC}/tools/lldb

pre-configure:
	@${SUBST_CMD} ${WRKSRC}/tools/clang/lib/Driver/ToolChains/OpenBSD.cpp
	@${SUBST_CMD} ${WRKSRC}/cmake/modules/LLVMProcessSources.cmake
	@${SUBST_CMD} ${WRKSRC}/tools/clang/tools/clang-shlib/CMakeLists.txt
	@${SUBST_CMD} ${WRKSRC}/tools/llvm-shlib/CMakeLists.txt
	-@ln -s ${MODPY_BIN} ${WRKDIR}/bin/python

post-build:
	cd ${WRKSRC}/docs && \
	    make -f Makefile.sphinx man SPHINXBUILD="sphinx-build${MODPY_BIN_SUFFIX}"
	cd ${WRKSRC}/tools/clang/docs && \
	    make -f Makefile.sphinx man SPHINXBUILD="sphinx-build${MODPY_BIN_SUFFIX}"

post-install:
	${INSTALL_DATA_DIR} \
	    ${PREFIX}/lib/python${MODPY_VERSION}/site-packages/clang
	${INSTALL_DATA} ${WRKSRC}/tools/clang/bindings/python/clang/* \
	    ${PREFIX}/lib/python${MODPY_VERSION}/site-packages/clang
	${MODPY_BIN} ${MODPY_LIBDIR}/compileall.py \
	    ${PREFIX}/lib/libear/ \
	    ${PREFIX}/lib/libscanbuild/ \
	    ${PREFIX}/lib/python${MODPY_VERSION}/site-packages/ \
	    ${PREFIX}/share/
	${INSTALL_DATA} ${WRKSRC}/docs/_build/man/* \
	    ${PREFIX}/man/man1
	${INSTALL_DATA} ${WRKSRC}/tools/clang/docs/_build/man/clang.1 \
	    ${PREFIX}/man/man1
	# lit and FileCheck are not installed
	@rm ${PREFIX}/man/man1/lit.1
	@rm ${PREFIX}/man/man1/FileCheck.1
	ln -fs ${TRUEPREFIX}/lib/liblldb.so.${LIBlldb_VERSION} \
	    ${PREFIX}/lib/python${MODPY_VERSION}/site-packages/lldb/_lldb.so

.include <bsd.port.mk>
