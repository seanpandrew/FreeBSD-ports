# Created by: Piotr Kubaj <pkubaj@anongoth.pl>
# $FreeBSD$

PORTNAME=	dbus-glib
PORTVERSION=	0.100
PORTREVISION=	1
CATEGORIES=	devel linux

MAINTAINER=	emulation@FreeBSD.org
COMMENT=	GLib bindings for D-Bus (Linux CentOS ${LINUX_DIST_VER})

CONFLICTS=      linux-c6-${PORTNAME}-[0-9]*

DESCR=		${.CURDIR}/../${PORTNAME}/pkg-descr
RPMVERSION=	7.el7
USES=		linux:c7
USE_LDCONFIG=	yes
USE_LINUX=	dbuslibs expat
USE_LINUX_RPM=	yes

.include <bsd.port.mk>
