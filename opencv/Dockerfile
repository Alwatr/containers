FROM ghcr.io/alwatr/alpine:3.19.1

ARG RUNTIME_DEPS='libpng-dev libjpeg-turbo libwebp tiff openexr jasper openblas libx11-dev zlib'
ARG BUILD_DEPS='xz wget unzip cmake build-base python3 linux-headers libjpeg-turbo-dev libwebp-dev tiff-dev openexr-dev jasper-dev openblas-dev zlib-dev'
ARG OPENCV_VERSION=4.8.1
ARG DLIB_VERSION=19.24.2
ARG LIB_PREFIX=/usr/local

ENV OPENCV_VERSION=${OPENCV_VERSION} \
    DLIB_VERSION=${DLIB_VERSION} \
    LIB_PREFIX=${LIB_PREFIX} \
    OPENCV4NODEJS_DISABLE_AUTOBUILD=1 \
    DLIB_INCLUDE_DIR=${LIB_PREFIX}/include \
    DLIB_LIB_DIR=${LIB_PREFIX}/lib

RUN apk add --upgrade --no-cache --virtual .build-dependencies $BUILD_DEPS \
  && wget -q https://github.com/opencv/opencv/archive/${OPENCV_VERSION}.zip -O opencv.zip \
  && wget -q https://github.com/opencv/opencv_contrib/archive/${OPENCV_VERSION}.zip -O opencv_contrib.zip \
  && wget -q https://github.com/davisking/dlib/archive/v${DLIB_VERSION}.zip -O dlib.zip \
  && mkdir /opencv \
  && mv opencv.zip opencv_contrib.zip /opencv \
  && cd /opencv \
  && unzip -q opencv.zip \
  && mv opencv-${OPENCV_VERSION} opencv \
  && unzip -q opencv_contrib.zip \
  && mv opencv_contrib-${OPENCV_VERSION} opencv_contrib \
  && ls -la \
  && mkdir opencv/build \
  && cd opencv/build \
  && opencv_cmake_flags="-D CMAKE_BUILD_TYPE=RELEASE \
    -D BUILD_DOCS=OFF \
    -D BUILD_TESTS=OFF \
    -D BUILD_PERF_TESTS=OFF \
    -D BUILD_JAVA=OFF \
    -D BUILD_opencv_apps=OFF \
    -D BUILD_opencv_aruco=OFF \
    -D BUILD_opencv_bgsegm=OFF \
    -D BUILD_opencv_bioinspired=OFF \
    -D BUILD_opencv_ccalib=OFF \
    -D BUILD_opencv_datasets=OFF \
    -D BUILD_opencv_dnn_objdetect=OFF \
    -D BUILD_opencv_dpm=OFF \
    -D BUILD_opencv_fuzzy=OFF \
    -D BUILD_opencv_hfs=OFF \
    -D BUILD_opencv_java_bindings_generator=OFF \
    -D BUILD_opencv_js=OFF \
    -D BUILD_opencv_img_hash=OFF \
    -D BUILD_opencv_line_descriptor=OFF \
    -D BUILD_opencv_optflow=OFF \
    -D BUILD_opencv_phase_unwrapping=OFF \
    -D BUILD_opencv_python3=OFF \
    -D BUILD_opencv_python_bindings_generator=OFF \
    -D BUILD_opencv_reg=OFF \
    -D BUILD_opencv_rgbd=OFF \
    -D BUILD_opencv_saliency=OFF \
    -D BUILD_opencv_shape=OFF \
    -D BUILD_opencv_stereo=OFF \
    -D BUILD_opencv_stitching=OFF \
    -D BUILD_opencv_structured_light=OFF \
    -D BUILD_opencv_superres=OFF \
    -D BUILD_opencv_surface_matching=OFF \
    -D BUILD_opencv_ts=OFF \
    -D BUILD_opencv_xobjdetect=OFF \
    -D BUILD_opencv_xphoto=OFF \
    -D CMAKE_INSTALL_PREFIX=$LIB_PREFIX \
    -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules" \
  && cmake $opencv_cmake_flags .. \
  && make -j $(nproc) \
  && cd /opencv/opencv/build \
  && make install \
  && cd / \
  && rm -rf /opencv \
  && dlib_cmake_flags="-D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=$LIB_PREFIX \
    -D DLIB_NO_GUI_SUPPORT=OFF \
    -D DLIB_USE_BLAS=ON \
    -D DLIB_PNG_SUPPORT=ON \
    -D DLIB_JPEG_SUPPORT=ON \
    -D DLIB_USE_CUDA=OFF" \
  && unzip -q dlib.zip \
  && mv dlib-${DLIB_VERSION} dlib \
  && rm dlib.zip \
  && cd dlib \
  && mkdir -p build \
  && cd build \
  && cmake $dlib_cmake_flags .. \
  && make -j $(nproc) \
  && cd /dlib/build \
  && make install \
  && cp /dlib/dlib/*.txt $LIB_PREFIX/include/dlib/ \
  && cd / \
  && rm -rf /dlib \
  && apk del .build-dependencies \
  && apk add --upgrade --no-cache $RUNTIME_DEPS \
  && rm -rf /var/cache/apk /usr/share/man /usr/local/share/man /tmp/*

ARG BUILD_REV
ARG BUILD_DATE
LABEL org.opencontainers.image.title="alwatr/opencv" \
      org.opencontainers.image.description="Native OpenCV library, packaged by Alwatr." \
      org.opencontainers.image.base.name="ghcr.io/alwatr/alpine:3.19.1" \
      org.opencontainers.image.version="4.8.1" \
      org.opencontainers.image.ref.name="4.8.1-dlib19.24.2" \
      org.opencontainers.image.licenses="MIT" \
      org.opencontainers.image.created=${BUILD_DATE} \
      org.opencontainers.image.revision=${BUILD_REV} \
      org.opencontainers.image.vendor="Alwatr" \
      org.opencontainers.image.source="https://github.com/Alwatr/containers/tree/next/opencv" \
      org.opencontainers.image.url="https://github.com/Alwatr/containers/tree/next/opencv" \
      org.opencontainers.image.documentation="https://github.com/Alwatr/containers/tree/next/opencv" \
      org.opencontainers.image.authors="S. Ali Mihandoost <ali.mihandoost@gmail.com> (https://ali.mihandoost.com), S. Amir Mohammad Najafi <njfamirm@gmail.com> (https://njfamirm.ir/)" \
      cloud.alwatr.image.version.full="4.8.1" \
      cloud.alwatr.image.version.short="4"
