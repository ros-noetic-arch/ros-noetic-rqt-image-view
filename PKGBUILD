pkgdesc="ROS - rqt_image_view provides a GUI plugin for displaying images using image_transport."
url='https://wiki.ros.org/rqt_image_view'

pkgname='ros-noetic-rqt-image-view'
pkgver='0.4.17'
arch=('i686' 'x86_64' 'aarch64' 'armv7h' 'armv6h')
pkgrel=2
license=('BSD')

ros_makedepends=(
	ros-noetic-rqt-gui-cpp
	ros-noetic-geometry-msgs
	ros-noetic-catkin
	ros-noetic-cv-bridge
	ros-noetic-rqt-gui
	ros-noetic-sensor-msgs
	ros-noetic-image-transport
)

makedepends=(
	'cmake'
	'ros-build-tools'
    'boost'
	${ros_makedepends[@]}
	qt5-base
)

ros_depends=(
	ros-noetic-rqt-gui-cpp
	ros-noetic-geometry-msgs
	ros-noetic-cv-bridge
	ros-noetic-rqt-gui
	ros-noetic-sensor-msgs
	ros-noetic-image-transport
)

depends=(
	${ros_depends[@]}
)

_commit="3803409bd001ca0583f8cc2a80941f53488afc2c"
_dir="rqt_image_view-${_commit}/"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros-visualization/rqt_image_view/archive/${_commit}.tar.gz")
sha256sums=('e1678c198dc92d5e4b5b3a7c4485c9f9ac20a5d04f492063430ae4925fdce6a7')

build() {
	# Use ROS environment variables.
	source /usr/share/ros-build-tools/clear-ros-env.sh
	[ -f /opt/ros/noetic/setup.bash ] && source /opt/ros/noetic/setup.bash

	# Create the build directory.
	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
	cd ${srcdir}/build

	# Build the project.
	cmake ${srcdir}/${_dir} \
		-DCATKIN_BUILD_BINARY_PACKAGE=ON \
		-DCMAKE_INSTALL_PREFIX=/opt/ros/noetic \
		-DPYTHON_EXECUTABLE=/usr/bin/python \
        -DCMAKE_CXX_STANDARD=17 \
		-DSETUPTOOLS_DEB_LAYOUT=OFF
	make
}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}
