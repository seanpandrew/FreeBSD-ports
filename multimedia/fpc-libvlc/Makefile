# Created by: Alonso Cardenas Marquez <acm@FreeBSD.org>
# $FreeBSD$

PORTREVISION=	1
CATEGORIES=	multimedia lang
PKGNAMESUFFIX=	-libvlc

COMMENT=	Free Pascal interface to vlc media player library

USE_FPC=	fcl-base fcl-res rtl-objpas

MASTERDIR=	${.CURDIR}/../../lang/fpc
WRKUNITDIR=	${FPCSRCDIR}/packages/${PKGNAMESUFFIX:S/-//}
EXTRACTUNITDIR=	${WRKUNITDIR}

OPTIONS_DEFINE=	VLC
VLC_DESC=	Install vlc media player
OPTIONS_DEFAULT=	VLC

VLC_RUN_DEPENDS=	vlc:multimedia/vlc

.include "${MASTERDIR}/Makefile"
