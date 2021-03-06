# $FreeBSD$

PORTNAME=	erlang
PORTVERSION=	19.3.6.1
PORTEPOCH=	1
CATEGORIES=	lang parallel java
MASTER_SITES=	http://www.erlang.org/download/:erlangorg		\
		http://erlang.stacken.kth.se/download/:erlangorg	\
		http://www.csd.uu.se/ftp/mirror/erlang/download/:erlangorg
PKGNAMESUFFIX=	-java
DISTNAME=	otp_src_${ERL_RELEASE}
DISTFILES=	${DISTNAME}${EXTRACT_SUFX}:erlangorg
DIST_SUBDIR=	erlang
EXTRACT_ONLY=	${DISTNAME}${EXTRACT_SUFX}

PATCH_SITES=	http://olgeni.olgeni.com/~olgeni/distfiles/ \
		LOCAL/olgeni
PATCHFILES=	patch-otp-19.3.1 patch-otp-19.3.2 patch-otp-19.3.3 \
		patch-otp-19.3.4 patch-otp-19.3.5 patch-otp-19.3.6 \
		patch-otp-19.3.6.1 patch-otp-19.3.6.2

MAINTAINER=	olgeni@FreeBSD.org
COMMENT=	Erlang interface for Java

LICENSE=	APACHE20

RUN_DEPENDS=	${LOCALBASE}/bin/erl:lang/erlang

WRKSRC=		${WRKDIR}/otp_src_${ERL_RELEASE}

PLIST_SUB=	APP_VERSION=${APP_VERSION}

MAKE_JOBS_UNSAFE=yes

OPTIONS_DEFINE=	DOCS

ERL_RELEASE=	19.3

USES=		gmake ncurses perl5
USE_PERL5=	build
GNU_CONFIGURE=	yes
LDFLAGS+=	-L${LOCALBASE}/lib

APP_VERSION=	1.7.1
APP_DIR=	${PREFIX}/lib/erlang/lib/jinterface-${APP_VERSION}

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MDOCS}
DISTFILES+=	${ERLANG_DOCS}:erlangorg
.endif

CONFIGURE_ARGS+=--enable-threads --without-odbc --with-javac
CONFIGURE_ENV+=	ac_cv_prog_JAVAC="${JAVAC}"

USE_JAVA=	yes

ERLANG_DOCS=	otp_doc_html_${ERL_RELEASE}.tar.gz

do-build:
	@${MKDIR} ${WRKSRC}/lib/jinterface/ebin
	cd ${WRKSRC}/lib/jinterface && ${GMAKE} ERL_TOP=${WRKSRC} TARGET=${CONFIGURE_TARGET}
	${RM} -r ${WRKSRC}/lib/jinterface/priv/com

do-install:
	@${MKDIR} ${STAGEDIR}${APP_DIR}
	@${MKDIR} ${STAGEDIR}${APP_DIR}/priv
	cd ${WRKSRC}/lib/jinterface && ${COPYTREE_SHARE} ebin ${STAGEDIR}${APP_DIR}
	cd ${WRKSRC}/lib/jinterface && ${COPYTREE_SHARE} java_src ${STAGEDIR}${APP_DIR}
	${INSTALL_DATA} ${WRKSRC}/lib/jinterface/priv/OtpErlang.jar ${STAGEDIR}${APP_DIR}/priv

do-install-DOCS-on:
	cd ${WRKSRC}/lib/jinterface && ${COPYTREE_SHARE} doc ${STAGEDIR}${APP_DIR}
	${TAR} --unlink -xzpf ${DISTDIR}/${DIST_SUBDIR}/${ERLANG_DOCS} \
		-C ${STAGEDIR}${PREFIX}/lib/erlang lib/jinterface-${APP_VERSION}
	@${FIND} ${STAGEDIR}${APP_DIR} -type d -empty -delete

.include <bsd.port.mk>
