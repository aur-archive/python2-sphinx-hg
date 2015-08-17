# Maintainer: Jonas Haag <jonas@lophus.org>
# Original contributor: Mineo <the_mineo at web dot de>

pkgname=python2-sphinx-hg
pkgver=20110304
pkgrel=1
pkgdesc="development version of Sphinx, *the* documentation generator"
url="http://sphinx.pocoo.org/latest/"
license="BSD"
arch=('i686' 'x86_64')
depends=('setuptools' 'python2-pygments' 'python-jinja2')
makedepends=('mercurial')
provides=('python-sphinx')

_hgroot="http://bitbucket.org/birkenfeld/sphinx"
_hgname="sphinx"

build() {
	cd $startdir/src
	msg "Connecting to $_hgroot server..."

	if [ -d $startdir/src/$_hgname ] ; then
		cd $_hgname && hg pull && hg update
		msg "The local files are updated."
	else
		hg clone $_hgroot
	fi

	msg "Mercurial checkout done or server timeout"
	msg "Copying files..."

	cp -r $startdir/src/$_hgname $startdir/src/$_hgname-build
	cd $startdir/src/$_hgname-build

  python2 setup.py install --root=$startdir/pkg || return 1
}

