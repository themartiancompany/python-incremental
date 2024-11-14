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
  'fbc0b123038341a788789aa513c93dfa08592881ea89aafebdd5b21917a9888f7a7d54d7765c105eb362559391ef45f15d8ef98278b0e75c84fce7d83febf5f0'
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
