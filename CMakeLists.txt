cmake_minimum_required(VERSION 2.8.3)
project(ukf_catkin)

find_package(catkin_simple REQUIRED)
catkin_simple()

include(ExternalProject)

# The configure step fails at catkin_package() if this directory
# doesn't exist yet. Create it at configure time!

ExternalProject_Add(ukf_src
  GIT_REPOSITORY https://github.com/KITcar-Team/ukf.git
  GIT_TAG d2c0208057982d4ceb925f0bff3ef0a972eb35cf
  CONFIGURE_COMMAND ""
  BUILD_COMMAND ""
  INSTALL_COMMAND pwd && cp -r ../ukf_src/include/UKF ${CATKIN_DEVEL_PREFIX}/include/UKF/
)

include_directories(${CATKIN_DEVEL_PREFIX}/include/)

cs_install()

cs_export(INCLUDE_DIRS ${CATKIN_DEVEL_PREFIX}/include)
