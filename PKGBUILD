# Contributor: and <and@ebrilo.jp>
license=('unknown')
arch=('i686')
pkgname=rstudio
pkgver=1.0.241
pkgrel=1
pkgdesc="R-Studio for Linux is powerful and cost-effective data recovery software. This is DEMO version limited to files smaller than 64 KB. Enter your registration key into this version to unlock the full version of R-Studio for Linux."
url=http://www.r-tt.com/data_recovery_linux
makedepends=('rpmextract')
source=(http://www.r-tt.com/downloads/rsl_en_1_i386.rpm)
md5sums=('de3523827e6814c47a0d65aba766588a')

build() {
cd "${pkgdir}"
rpmextract.sh "../rsl_en_1_i386.rpm"
mv usr/local opt
install -d usr/share/applications
sed 's/\/usr\/local/\/opt/g' opt/R-Studio/share/rtt-rstudio.desktop | sed 's/Icon=rtt-rstudio/Icon=\/opt\/R-Studio\/share\/logo_48.png/g' > usr/share/applications/rtt-rstudio.desktop
rm -f opt/R-Studio/share/rtt-rstudio.desktop
rm -rf usr/share/menu
rm -f usr/bin/rstudio
sed 's/\/usr\/local/\/opt/g' opt/R-Studio/bin/rstudio | sed 's/sudo/su/g' | sed 's/\/opt\/R-Studio\/share\/rtt-rstudio.desktop/\/usr\/share\/applications\/rtt-rstudio.desktop/g' > usr/bin/rstudio
rm -f opt/R-Studio/bin/rstudio
mv usr/bin/rstudio opt/R-Studio/bin/rstudio
chmod 755 opt/R-Studio/bin/rstudio
ln -s /opt/R-Studio/bin/rstudio usr/bin/rstudio
rm -f opt/R-Studio/lib/librs_linux_r.so
ln -s rs_linux_r.so opt/R-Studio/lib/librs_linux_r.so
}
