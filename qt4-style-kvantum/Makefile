# $FreeBSD$

PORTNAME=	kvantum

USE_GITHUB=	yes
GH_ACCOUNT=	tsujan
GH_PROJECT=	Kvantum
GH_TAGNAME=	${GH_COMMIT}
GH_COMMIT=	286b4fc

DISTVERSION=	0.8.17
PORTREVISION=	4
CATEGORIES=	x11-themes
PKGNAMEPREFIX=	qt4-style-
DISTNAME=	Kvantum-${DISTVERSION}_${PORTREVISION}

MAINTAINER=	d.akiyakov@gmail.com
COMMENT=	SVG-based theme engine for Qt4/Qt5 and KDE

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/COPYING

USES=		qmake:outsource
USE_QT4=	gui svg rcc_build uic_build moc_build

WRKSRC=		${WRKDIR}/${GH_ACCOUNT}-${GH_PROJECT}-${GH_TAGNAME}/${GH_PROJECT}

.include <bsd.port.mk>
