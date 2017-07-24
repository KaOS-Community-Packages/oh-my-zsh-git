pkgname=oh-my-zsh-git
pkgver=r4319.d848c948
pkgrel=1
pkgdesc="A community-driven framework for managing your zsh configuration."
arch=('x86_64')
url='https://github.com/robbyrussell/oh-my-zsh'
license=('MIT')
depends=('zsh')
makedepends=('git')
optdepends=('ruby: for some plugin functionality')
install=${pkgname}.install
source=("${pkgname}::git+git://github.com/robbyrussell/oh-my-zsh.git"
        '0001-zshrc.patch')
sha256sums=('SKIP'
            '9b77769319944f394a36f07b9abb296d24fe643c03b8eead74e10b7da52002b1')
# conflicts=('grml-zsh-config'
#            'grml-zsh-config-git')

pkgver() {
  cd ${pkgname}
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  cd "${srcdir}/${pkgname}"
  cp "templates/zshrc.zsh-template" "zshrc"
  patch -p1 < "${srcdir}/0001-zshrc.patch"
}

package() {
  cd "${srcdir}/${pkgname}"

  mkdir -p "${pkgdir}/usr/share/oh-my-zsh"
  install -D -m644 "LICENSE.txt" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  cp -r * "${pkgdir}/usr/share/oh-my-zsh/"
}

# vim:set ts=2 sw=2 et:
