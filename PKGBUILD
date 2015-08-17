# Contributor: Iwan 'qubodup' Gabovitch <qubodup@gmail.com>
# Contributer: giacomogiorgianni@gmail.com

pkgname=ogreoggsound-svn
pkgver=420
pkgrel=1
pkgdesc="OpenAL wrapper. Supports OGG/WAV. Integrates into OGRE."
url="http://sourceforge.net/projects/ogreoggsound/"
arch=('i686' 'x86_64')
license=('LGPL')
depends=('ogre>=1.7.3' 'openal' 'boost>=1.43')
makedepends=('cmake>=2.6.4')

build() {
    svndir=$startdir/src/ogreoggsound-svn
    svnroot=https://ogreoggsound.svn.sourceforge.net/svnroot/ogreoggsound/trunk

    if [ ! -d $svndir ]; then
        svn co -r $pkgver $svnroot $svndir || return 1
    else
        svn up -r $pkgver $svndir || return 1
    fi

    cd $svndir
    cmake . || return 1
    sed -i '2583 a\	boost::recursive_mutex mMutex;' $svndir/src/ogreoggsoundmanager.cpp
    sed -i '947 a\	boost::recursive_mutex mMutex;' $svndir/src/ogreoggsoundmanager.cpp
    make || return 1
	make DESTDIR=$pkgdir install
}

