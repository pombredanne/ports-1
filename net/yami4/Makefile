# $FreeBSD$

PORTNAME=	yami4
PORTVERSION=	1.10.0
CATEGORIES=	net
MASTER_SITES=	http://www.inspirel.com/yami4/files/
DISTNAME=	yami4-gpl-1.10.0

MAINTAINER=	prog@msobczak.com
COMMENT=	Messaging library for distributed systems

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/gpl-3.0.txt

BROKEN_powerpc64=	Does not build

# USES=		compiler:c++11-lib

.include <bsd.port.pre.mk>

.if ${OPSYS} == FreeBSD && ${OSVERSION} < 1000000
BROKEN=	Does only compile with FreeBSD 10.x or higher
.endif

do-build :
	cd ${WRKSRC}/src/core; make
	cd ${WRKSRC}/src/cpp; make

do-install :
	${MKDIR} ${STAGEDIR}${PREFIX}/share/doc/yami4
	${MKDIR} ${STAGEDIR}${PREFIX}/share/doc/yami4/core
	${MKDIR} ${STAGEDIR}${PREFIX}/share/doc/yami4/cpp
	(cd ${WRKSRC}/doc/core && ${COPYTREE_SHARE} . ${STAGEDIR}${PREFIX}/share/doc/yami4/core)
	(cd ${WRKSRC}/doc/cpp && ${COPYTREE_SHARE} . ${STAGEDIR}${PREFIX}/share/doc/yami4/cpp)
	(cd ${WRKSRC}/include && ${COPYTREE_SHARE} yami4-core ${STAGEDIR}${PREFIX}/include)
	(cd ${WRKSRC}/include && ${COPYTREE_SHARE} yami4-cpp ${STAGEDIR}${PREFIX}/include)
	(cd ${WRKSRC}/lib && ${INSTALL_DATA} *.a ${STAGEDIR}${PREFIX}/lib)

.include <bsd.port.post.mk>
