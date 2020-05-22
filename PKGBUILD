# Script generated with create_pkgbuild.py
# For more information: https://github.com/ros-melodic-arch/ros-build-tools-py3
pkgdesc="ROS - Components of MoveIt! connecting to occupancy map."
url='https://moveit.ros.org/'

pkgname='ros-melodic-moveit-ros-occupancy-map-monitor'
pkgver='1.0.3'
arch=('i686' 'x86_64' 'aarch64' 'armv7h' 'armv6h')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-melodic-catkin
                 ros-melodic-geometric-shapes
                 ros-melodic-tf2-ros
                 ros-melodic-moveit-core
                 ros-melodic-moveit-msgs
                 ros-melodic-pluginlib
                 ros-melodic-octomap)
makedepends=('cmake' 'ros-build-tools'
             ${ros_makedepends[@]}
             eigen3)

ros_depends=(ros-melodic-geometric-shapes
             ros-melodic-tf2-ros
             ros-melodic-moveit-core
             ros-melodic-moveit-msgs
             ros-melodic-pluginlib
             ros-melodic-octomap)
depends=(${ros_depends[@]})

_dir="moveit-${pkgver}/moveit_ros/occupancy_map_monitor"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros-planning/moveit/archive/${pkgver}.tar.gz")
sha256sums=('b0ac91cd4c4dc29d9bd5e3885a1a457252495b3f2bedb46ddfe04154f5ac2358')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 3 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
          -DCMAKE_BUILD_TYPE=Release \
          -DCATKIN_BUILD_BINARY_PACKAGE=ON \
          -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
          -DPYTHON_EXECUTABLE=/usr/bin/python3 \
          -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

