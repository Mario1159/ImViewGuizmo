cmake_minimum_required(VERSION 3.22)

project(ImViewGuizmo LANGUAGES CXX)

add_library(imviewguizmo INTERFACE)
add_library(imviewguizmo::imviewguizmo ALIAS imviewguizmo)

target_include_directories(imviewguizmo
  INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}>
    $<INSTALL_INTERFACE:include>
)

target_sources(imviewguizmo
  INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/ImViewGuizmo.h>
)

target_compile_features(imviewguizmo INTERFACE cxx_std_17)

include(GNUInstallDirs)

install(
  TARGETS imviewguizmo
  EXPORT imviewguizmoTargets
)

install(
  FILES ${CMAKE_CURRENT_LIST_DIR}/ImViewGuizmo.h
  DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)

install(
  EXPORT imviewguizmoTargets
  NAMESPACE imviewguizmo::
  DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/imviewguizmo
)
