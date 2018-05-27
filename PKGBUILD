# Maintainer: Kyle Keen <keenerd@gmail.com>
# Contributor: Germán Osella Massa <gosella@gmail.com>

pkgbase=python-more-itertools
pkgname=('python-more-itertools' 'python2-more-itertools')
pkgver=4.2.0
pkgrel=1
pkgdesc='More routines for operating on iterables, beyond itertools'
arch=('any')
url='https://github.com/erikrose/more-itertools'
#url='https://pypi.python.org/pypi/more-itertools'
license=('MIT')
depends=('python')
makedepends=('python-setuptools' 'python2-setuptools' 'python2-six')
source=("https://files.pythonhosted.org/packages/source/m/more-itertools/more-itertools-$pkgver.tar.gz")
md5sums=('5629c955d17df328ec534989f0649369')

prepare() {
  cp -R "more-itertools-$pkgver" "py2-more-itertools-$pkgver"
}

package_python-more-itertools() {
  cd "$srcdir/more-itertools-$pkgver"
  python3 setup.py install --root="$pkgdir/" --optimize=0
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

package_python2-more-itertools() {
  depends=('python2' 'python2-six')
  cd "$srcdir/py2-more-itertools-$pkgver"
  python2 setup.py install --root="$pkgdir/" --optimize=0
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
