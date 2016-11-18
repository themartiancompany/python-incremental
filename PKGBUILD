# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgbase=python-incremental
pkgname=('python-incremental' 'python2-incremental')
pkgver=16.10.1
pkgrel=1
pkgdesc='A small library that versions your Python projects'
arch=('any')
license=('MIT')
url='https://github.com/hawkowl/incremental'
makedepends=('python-setuptools' 'python2-setuptools' 'python-click' 'python2-click'
             'python-twisted' 'python2-twisted' 'git')
checkdepends=('python-pytest-runner' 'python2-pytest-runner')
source=("git+https://github.com/hawkowl/incremental.git#tag=incremental-$pkgver")
md5sums=('SKIP')

prepare() {
  cp -a incremental{,-py2}
}

build() {
  cd "$srcdir"/incremental
  python setup.py build

  cd "$srcdir"/incremental-py2
  python2 setup.py build
}

check() {
  cd "$srcdir"/incremental
  LC_CTYPE=en_US.UTF-8 python setup.py ptr

  cd "$srcdir"/incremental-py2
  python2 setup.py ptr
}

package_python-incremental() {
  depends=('python-click' 'python-twisted')

  cd incremental
  python setup.py install --root="$pkgdir" --optimize=1
  install -D -m644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

package_python2-incremental() {
  depends=('python2-click' 'python2-twisted')

  cd incremental-py2
  python2 setup.py install --root="$pkgdir" --optimize=1
  install -D -m644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

# vim:set ts=2 sw=2 et:
