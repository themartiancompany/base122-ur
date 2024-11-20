# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Truocolo <truocolo@aol.com>

_pkg="base122"
_Pkg="lib${_pkg}"
pkgname="${_pkg}"
pkgver=2024.11.20
_commit="e71b8a65030dcf112911eebc11c40f2ea4ce0bab"
pkgrel=1
pkgdesc="Base122 library"
arch=(
  x86_64
  arm
  aarch64
  i686
  pentium4
  powerpc
  mips
  armv6l
)
_http="https://github.com"
_ns="kevinAlbs"
url="${_http}/${_ns}/${_Pkg}"
license=(
  'Apache-2.0'
)
depends=(
  # glibc
)
makedepends=(
  cmake
  git
)
provides=(
  "${_Pkg}=${pkgver}"
  "${_Pkg}.so=${pkgver}"
)
conflicts=(
  "${_Pkg}=${pkgver}"
)
_tag="${_commit}"
_tag_name="commit"
_tarname="${_Pkg}-${_tag}"
source=(
  # "${_tarname}::git+${url}#${_tag_name}=${_tag}"
  "${_tarname}.zip::${url}/archive/${_commit}.zip"
)
sha256sums=(
  # 'SKIP'
  'd90f811897b110b67fdc826e86cf0f54f0d2cca384d408eece88548f7f189218'
)
b2sums=(
  'SKIP'
)
validpgpkeys=(
)

build() {
  local \
    _cmake_opts=()
  _cmake_opts=(
    # -DCMAKE_INSTALL_PREFIX=/usr
    # -DCMAKE_BUILD_TYPE=None
    # -W
    #   no-dev
    -B
      build
  )
  cmake \
    "${_cmake_opts[@]}" \
    -S \
      "${_tarname}"
  make \
    VERBOSE=1 \
    -C \
      build
}

check() {
  make \
    VERBOSE=1 \
    -C \
      build \
    test
}

package() {
  make \
    VERBOSE=1 \
    DESTDIR="${pkgdir}" \
    -C \
      build \
    install
  install \
    -vDm644 \
    "${_tarname}/LICENSE" \
    -t \
      "${pkgdir}/usr/share/licenses/${pkgname}/"
  install \
    -vDm644 \
    "${_tarname}/"{'README.md'} \
    -t \
    "${pkgdir}/usr/share/doc/${pkgname}/"
}

# vim: ft=sh syn=sh et
