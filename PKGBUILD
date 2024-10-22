# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: George Rawlinson <grawlinson@archlinux.org>
# Maintainer: Kyle Keen <keenerd@gmail.com>
# Contributor: Germán Osella Massa <gosella@gmail.com>

_git="true"
_os="$( \
  uname \
    -o)"
if [[ "${_os}" == "Android" ]]; then
  _git="false"
fi
_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pkg="more-itertools"
pkgname="${_py}-${_pkg}"
pkgver=10.1.0
pkgrel=1
pkgdesc='More routines for operating on iterables, beyond itertools'
arch=('any')
_http="https://github.com"
url="${_http}/${_pkg}/${_pkg}"
license=(
  'MIT'
)
depends=(
  "${_py}>=${_pymajver}"
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-wheel"
  "${_py}-flit-core"
)
_commit='266ebdcf9027b7bb6ab72f8cd4585804c1e1547e'
_tag="${_commit}"
_tag_name="commit"
_tarname="${_pkg}-${pkgver}"
_pypi="https://pypi.io/packages/source"
if [[ "${_git}" == "true" ]]; then
  makedepends+=(
    'git'
  )
  _src="${_tarname}::git+${url}.git#${_tag_name}=${_tag}"
  _sum="SKIP"
elif [[ "${_git}" == "false" ]]; then
  _src="${_tarname}.tar.gz::${_pypi}/${_pkg::1}/${_pkg}/${_pkg}-${pkgver}.tar.gz"
  _sum="457eb62d735ac0d0f4a93a6a79c747ac965c1af394a1d894c4f80abfa0a94de76d804c7e68d4122fabf09b7c8e2f1d59bb1c43ff54c7cd5c2d52b5a1280b0290"
fi
source=(
  "${_src}"
)
b2sums=(
  "${_sum}"
)

pkgver() {
  local \
    _pkgver
  _pkgver="${pkgver}"
  if [[ "${_git}" == "true" ]]; then
    cd \
      "${_tarname}"
    _pkgver="$( \
      git \
        describe \
        --tags | \
        sed \
        's/^v//')"
  fi
  echo \
    "${_pkgver}"
}

build() {
  cd \
    "${_tarname}"
  "${_py}" \
    -m \
      build \
    --wheel \
    --no-isolation
}

check() {
  cd \
    "${_tarname}"
  "${_py}" \
    -m \
      unittest
}

package() {
  cd \
    "${_tarname}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  # license
  install \
    -vDm644 \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}" \
    LICENSE
}

# vim:set ts=2 sw=2 et:
