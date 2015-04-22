# $FreeBSD$

PORTNAME=	kvantum
DISTVERSION=	0.8.19
CATEGORIES=	x11-themes kde
PKGNAMEPREFIX=	qt4-style-

MAINTAINER=	d.akiyakov@gmail.com
COMMENT=	SVG-based theme engine for Qt4/Qt5 and KDE

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/COPYING

USE_GITHUB=	yes
GH_ACCOUNT=	tsujan
GH_PROJECT=	Kvantum
GH_TAGNAME=	bd98e81

OPTIONS_DEFINE=	DOCS EXAMPLES

INSTALLDOCS=	doc/Theme-Making.pdf doc/Theme-Config.pdf doc/Theme-Config \
		ChangeLog README
PORTDOCS=	Theme-Making.pdf Theme-Config.pdf Theme-Config ChangeLog README
PORTEXAMPLES=	Glassy default.svg

WRKSRC=		${WRKDIR}/${GH_PROJECT}-${GH_TAGNAME}/${GH_PROJECT}

USES=		qmake:outsource
USE_QT4=	gui svg rcc_build uic_build moc_build

.include <bsd.port.options.mk>

post-install:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
.for i in ${INSTALLDOCS}
	${INSTALL_DATA} ${WRKSRC}/${i} ${STAGEDIR}${DOCSDIR}
.endfor
.endif
.if ${PORT_OPTIONS:MEXAMPLES}
	@${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
	cd ${WRKSRC}/doc && ${COPYTREE_SHARE} Glassy ${STAGEDIR}${EXAMPLESDIR}
	${INSTALL_DATA} ${WRKSRC}/doc/default.svg ${STAGEDIR}${EXAMPLESDIR}
.endif

.include <bsd.port.mk>
