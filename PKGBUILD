#!/bin/bash

# Disable various shellcheck rules that produce false 
# Repository rules should be added to the .shellcheckr
# repository root directory, see https://github.com/ko
# and https://archiv8.github.io for further informatio
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <archiv8@artisteducator.com>
# Contributor: Ross Clark <archiv8@artisteducator.com>

java_=17
pkgname="jdk${java_}-graalvm-bin"
pkgver=22.0.0.2
pkgrel=1
pkgdesc="Universal virtual machine for running applications written in a variety of languages (JVM-based, LLVM-based, or other), Java ${java_} version"
arch=('x86_64'
      'aarch64')
url='https://www.graalvm.org/'
license=('custom')
depends=('java-runtime-common'
         'java-environment-common')
makedepends=()
provides=("java-runtime=${java_}"
          "java-environment=${java_}")
options=('staticlibs')
install="$pkgname.install"
source=('graalvm-rebuild-libpolyglot.hook')
sha512sums=('SKIP')
source_x86_64=("https://github.com/graalvm/graalvm-ce-builds/releases/download/vm-${pkgver}/graalvm-ce-java${java_}-linux-amd64-${pkgver}.tar.gz")
source_aarch64=("https://github.com/graalvm/graalvm-ce-builds/releases/download/vm-${pkgver}/graalvm-ce-java${java_}-linux-aarch64-${pkgver}.tar.gz")
sha512sums=('30765efa2e1115fc6fe32dbae12994e7397a54fa572a121fa010baf5f95539ffaf39dbdea730fa137856aee591ff2d0f29f539cfd9608633408ba1687f561c1a')
sha512sums_x86_64=('eadcbb28a5817dc665701a22eb9795f61f142577cf85948088fcfc1bf8c10443185e1b1465a88fc038b981524e1bedfc2b26a482998dd472d0ffc6e4fe67ffaf')
sha512sums_aarch64=('9fc5c053cb7e60c2c4b9fea3ed61972bb654a37825c10d833c2b2f1ed8b8f235499ae3bab19af0a973b3922d31b02c68d8b1ee144f1214b4a8e6faca4f8a0fef')

package() {
    cd "graalvm-ce-java${java_}-${pkgver}"
    mkdir -p "$pkgdir/usr/lib/jvm/java-${java_}-graalvm/"
    cp -a -t "$pkgdir/usr/lib/jvm/java-${java_}-graalvm/" *
    install -DTm644 LICENSE.txt "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
    sed "s/JAVA/${java_}/g" < "../graalvm-rebuild-libpolyglot.hook" > "graalvm-jdk${java_}-rebuild-libpolyglot.hook"
    install -DTm644 "graalvm-jdk${java_}-rebuild-libpolyglot.hook" "$pkgdir/usr/share/libalpm/hooks/graalvm-jdk${java_}-rebuild-libpolyglot.hook"
}
