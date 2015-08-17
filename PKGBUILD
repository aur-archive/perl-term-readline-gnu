# CPAN Name  : Term-ReadLine-Gnu
# Maintainer : jason ryan <jasonwryan@gmail.com>
# Contributor: AUR Perl <aurperl@juster.info>
# Generator  : CPANPLUS::Dist::Arch 1.15

pkgname='perl-term-readline-gnu'
pkgver='1.20'
pkgrel='3'
pkgdesc="GNU Readline XS library wrapper"
arch=('i686' 'x86_64')
license=('PerlArtistic' 'GPL')
options=('!emptydirs')
depends=('perl>=5.7' 'readline>=2.1')
makedepends=()
url='http://search.cpan.org/dist/Term-ReadLine-Gnu'
source=('http://search.cpan.org/CPAN/authors/id/H/HA/HAYASHI/Term-ReadLine-Gnu-1.20.tar.gz'
  'termcap-bad-ncurses-good.patch')
md5sums=('fa33510193b89a2ada74fcef00816322'
  'a000706b89792f822b5ec20baa370910')
_distdir="${srcdir}/Term-ReadLine-Gnu-1.20"

build() {
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""                 \
      PERL_AUTOINSTALL=--skipdeps                            \
      PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'"     \
      PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
      MODULEBUILDRC=/dev/null

    cd "$_distdir"
    patch --forward -p1 < "${srcdir}/termcap-bad-ncurses-good.patch"
    /usr/bin/perl Makefile.PL
    make
  )
}

check() {
  cd "$_distdir"
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""
    make test
  )
}

package() {
  cd "$_distdir"
  make install
  find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}

