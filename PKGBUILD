# Maintainer: Alexander Baldeck <kth5@archlinuxppc.org>
# Contributor: Jochen Schalanda <jochen+aur@schalanda.name>
pkgname=mcollective
pkgver=2.6.1
pkgrel=1
pkgdesc="Framework to build server orchestration or parallel job execution systems"
arch=(any)
url="http://www.puppetlabs.com/mcollective/"
license=('APACHE')
depends=('ruby>=1.9' 'ruby-stomp' 'ruby-systemu')
source=("http://puppetlabs.com/downloads/mcollective/${pkgname}-${pkgver}.tar.gz"
        'mcollective@.service')
md5sums=('3ec56024d7af744fd8e90c2384f96de2'
         'f227a0798be70a09abd096ae96058ecf')

package() {
  cd ${pkgname}-${pkgver}

  install -Dm0755 bin/mcollectived "${pkgdir}/usr/bin/mcollectived"
  install -Dm0755 bin/mco "${pkgdir}/usr/bin/mco"
  install -Dm0640 etc/server.cfg.dist "${pkgdir}/etc/mcollective/server.cfg"
  install -Dm0644 etc/client.cfg.dist "${pkgdir}/etc/mcollective/client.cfg"
  install -Dm0644 etc/facts.yaml.dist "${pkgdir}/etc/mcollective/facts.yaml"
  install -Dm0644 etc/rpc-help.erb "${pkgdir}/etc/mcollective/rpc-help.erb"

  install -Dm0644 "${srcdir}/mcollective@.service" "${pkgdir}/usr/lib/systemd/system/mcollective@.service"

  install -dm0755 "${pkgdir}/usr/lib/ruby/site_ruby"
  install -dm0755 "${pkgdir}/usr/libexec/mcollective"
  cp -r lib/* "${pkgdir}/usr/lib/ruby/site_ruby"
  cp -r plugins/* "${pkgdir}/usr/libexec/mcollective"
}
