# Script generated with Bloom
pkgdesc="ROS - driver for the KUKA youBot robot"
url='http://github.com/youbot/youbot_driver'

pkgname='ros-kinetic-youbot-driver'
pkgver='1.1.0_1'
pkgrel=1
arch=('any')
license=('LGPLv2.1, modified BSD'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-rosconsole'
'ros-kinetic-roscpp'
)

depends=('ros-kinetic-rosconsole'
'ros-kinetic-roscpp'
)

conflicts=()
replaces=()

_dir=youbot_driver
source=()
md5sums=()

prepare() {
    cp -R $startdir/youbot_driver $srcdir/youbot_driver
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

