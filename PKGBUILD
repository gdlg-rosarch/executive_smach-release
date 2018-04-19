# Script generated with Bloom
pkgdesc="ROS - The smach_ros package contains extensions for the SMACH library to integrate it tightly with ROS. For example, SMACH-ROS can call ROS services, listen to ROS topics, and integrate with <a href="http://www.ros.org/wiki/actionlib">actionlib</a> both as a client, and a provider of action servers. SMACH is a new library that takes advantage of very old concepts in order to quickly create robust robot behavior with maintainable and modular code."


pkgname='ros-lunar-smach-ros'
pkgver='2.0.1_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-lunar-catkin'
'ros-lunar-rostest'
)

depends=('ros-lunar-actionlib'
'ros-lunar-actionlib-msgs'
'ros-lunar-rospy'
'ros-lunar-rostopic'
'ros-lunar-smach'
'ros-lunar-smach-msgs'
'ros-lunar-std-msgs'
'ros-lunar-std-srvs'
)

conflicts=()
replaces=()

_dir=smach_ros
source=()
md5sums=()

prepare() {
    cp -R $startdir/smach_ros $srcdir/smach_ros
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
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

