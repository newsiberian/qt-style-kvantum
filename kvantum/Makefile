# $FreeBSD$

PORTNAME=	kvantum
DISTVERSION=	0.8.23
CATEGORIES=	x11-themes

MAINTAINER=	d.akiyakov@gmail.com
COMMENT?=	SVG-based theme engine for Qt4/Qt5 and KDE

.if !defined(KVANTUM_SLAVE)
USES=		metaport

#OPTIONS_DEFINE=		DOCS EXAMPLES QT4
OPTIONS_DEFINE=		QT4
OPTIONS_SINGLE=		QT1
OPTIONS_SINGLE_QT1=	QT4_MANAGER QT5
OPTIONS_DEFAULT=	QT4 QT4_MANAGER

QT1_DESC=	Qt: additional support
QT4_MANAGER_DESC=	with engine manager for Qt 4

#QT4_RUN_DEPENDS=	qt4-style-kvantum>=${DISTVERSION}:/home/sohaam/tmp/kvantum/port/kvantum-qt4
#QT4_MANAGER_RUN_DEPENDS=	qt4-kvantummanager>=${DISTVERSION}:/home/sohaam/tmp/kvantum/port/kvantummanager-qt4
#QT5_RUN_DEPENDS=	qt5-style-kvantum>=${DISTVERSION}:/home/sohaam/tmp/kvantum/port/kvantum-qt5
QT4_RUN_DEPENDS=	qt4-style-kvantum>=${DISTVERSION}:${PORTSDIR}/x11-themes/kvantum-qt4
QT4_MANAGER_RUN_DEPENDS= qt4-kvantummanager>=${DISTVERSION}:${PORTSDIR}/x11-themes/kvantummanager-qt4
QT5_RUN_DEPENDS=	qt5-style-kvantum>=${DISTVERSION}:${PORTSDIR}/x11-themes/kvantum-qt5

.else  # !defined(KVANTUM_SLAVE)

LICENSE=	GPLv3

USE_GITHUB=	yes
GH_ACCOUNT=	tsujan
GH_PROJECT=	Kvantum
GH_TAGNAME=	7462d46

#INSTALLDOCS=	doc/Theme-Making.pdf doc/Theme-Config.pdf doc/Theme-Config \
#		ChangeLog README
#PORTDOCS=	Theme-Making.pdf Theme-Config.pdf Theme-Config ChangeLog README
#PORTEXAMPLES=	Glassy default.svg

WRKSRC=		${WRKDIR}/${GH_PROJECT}-${GH_TAGNAME}/${GH_PROJECT}
USES=		qmake:outsource

PLIST=		${PKGDIR}/pkg-plist.${KVANTUM_SLAVE}

#.include <bsd.port.options.mk>

.if ${KVANTUM_SLAVE} == "qt4"
PKGNAMEPREFIX=	qt4-style-
LICENSE_FILE=	${WRKSRC}/COPYING
USE_QT4=	gui svg rcc_build moc_build
PLIST_FILES=	${QT_PLUGINDIR_REL}/styles/libkvantum.so \
		share/kde4/apps/color-schemes/Kvantum.colors
.endif

.if ${KVANTUM_SLAVE} == "manager-qt4"
PKGNAMEPREFIX=	qt4-
PKGNAMESUFFIX=manager
LICENSE_FILE=	${WRKSRC}/COPYING
USE_QT4=	gui svg rcc_build uic_build moc_build
#BUILD_DEPENDS=	qt4-style-${PORTNAME}>=${DISTVERSION}:/home/sohaam/tmp/kvantum/port/kvantum-qt4
BUILD_DEPENDS=	qt4-style-${PORTNAME}>=${DISTVERSION}:${PORTSDIR}/x11-themes/kvantum-qt4
CONFLICTS=	qt5-style-${PORTNAME}-[0-9]*

do-configure:
.for dir in kvantummanager kvantumpreview
	@(cd ${WRKSRC}/${dir} && ${SETENV} ${QMAKE_ENV} ${QMAKE} ${QMAKE_ARGS})
.endfor

do-build:
.for dir in kvantummanager kvantumpreview
	@(cd ${WRKSRC}/${dir} && ${SETENV} ${MAKE_ENV} ${MAKE_CMD} \
		${MAKE_FLAGS} ${MAKEFILE} ${MAKE_ARGS} ${ALL_TARGET})
.endfor

do-install:
.for dir in kvantummanager kvantumpreview
	@(cd ${WRKSRC}/${dir} && ${SETENV} ${MAKE_ENV} ${MAKE} ${MAKE_FLAGS} \
		${MAKEFILE} ${MAKE_ARGS} ${INSTALL_TARGET})
.endfor
.endif

.if ${KVANTUM_SLAVE} == "qt5"
PKGNAMEPREFIX=	qt5-style-
LICENSE_FILE=	${WRKSRC}/COPYING
USE_QT5=	gui svg widgets x11extras buildtools_build
CONFLICTS=	qt4-${PORTNAME}manager-[0-9]*
.endif # qt5

#post-install:
#.if ${PORT_OPTIONS:MDOCS}
#	@${MKDIR} ${STAGEDIR}${DOCSDIR}
#.for i in ${INSTALLDOCS}
#	${INSTALL_DATA} ${WRKSRC}/${i} ${STAGEDIR}${DOCSDIR}
#.endfor
#.endif
#.if ${PORT_OPTIONS:MEXAMPLES}
#	@${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
#	cd ${WRKSRC}/doc && ${COPYTREE_SHARE} Glassy ${STAGEDIR}${EXAMPLESDIR}
#	${INSTALL_DATA} ${WRKSRC}/doc/default.svg ${STAGEDIR}${EXAMPLESDIR}
#.endif

.endif # !defined(KVANTUM_SLAVE)

.include <bsd.port.mk>
