# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Felix Yan <felixonmars@archlinux.org>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=incremental
pkgname="${_py}-${_pkg}"
pkgver=24.7.2
pkgrel=5
pkgdesc='A small library that versions your Python projects'
arch=(
  'any'
)
license=(
  'MIT'
)
depends=(
  "${_py}-click"
  "${_py}-setuptools"
  "${_py}-twisted"
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-wheel"
)
_http="https://github.com"
_ns="hawkowl"
url="${_http}/${_ns}/${_pkg}"
checkdepends=(
  "${_py}-pytest"
)
source=(
  "${url}/archive/${_pkg}-${pkgver}.tar.gz"
)
sha512sums=(
  'd76a4192299bfa94a84f2e126800f2898c9c56c6831b6fe945fb291151f62958416d6d8118c0ea7c3cefbb85da6a97dfe9a2f8b95b31062a0831e84d522014d8'
)

build() {
  ls
  cd \
    "${_pkg}-${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      build \
    --wheel \
    --no-isolation
}

check() {
  cd \
    "${_pkg}-${_pkg}-${pkgver}"
  pytest
}

package() {
  cd \
    "${_pkg}-${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  install \
    -Dm644 \
    LICENSE \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
}

# vim:set ts=2 sw=2 et:
