# $FreeBSD$

PORTNAME=	kvantum
DISTVERSION=	0.8.18
CATEGORIES=	x11-themes kde
PKGNAMEPREFIX=	qt4-style-

MAINTAINER=	d.akiyakov@gmail.com
COMMENT=	SVG-based theme engine for Qt4/Qt5 and KDE

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/COPYING

USE_GITHUB=	yes
GH_ACCOUNT=	tsujan
GH_PROJECT=	Kvantum
GH_TAGNAME=	${GH_COMMIT}
GH_COMMIT=	f7ec041

WRKSRC=		${WRKDIR}/${GH_ACCOUNT}-${GH_PROJECT}-${GH_TAGNAME}/${GH_PROJECT}

USES=		qmake:outsource
USE_QT4=	gui svg rcc_build uic_build moc_build

.include <bsd.port.mk>
