project(glog)
cmake_minimum_required(VERSION 2.8)
include_directories(${GLOG_P})
set(GLOG_P ${CMAKE_CURRENT_LIST_DIR}/src)
set(GLOG_FILES
  ${GLOG_P}/base/commandlineflags.h
  ${GLOG_P}/base/googleinit.h
  ${GLOG_P}/base/mutex.h
  ${GLOG_P}/utilities.h
  ${GLOG_P}/logging.cc
  ${GLOG_P}/raw_logging.cc
  ${GLOG_P}/utilities.cc
  ${GLOG_P}/vlog_is_on.cc
  )
if(WIN32)
  add_definitions(-D_CRT_SECURE_NO_WARNINGS)
  include_directories(${GLOG_P}/windows)
  set(GLOG_FILES ${GLOG_FILES}
    ${GLOG_P}/windows/config.h
    ${GLOG_P}/windows/port.h
    ${GLOG_P}/windows/port.cc
    ${GLOG_P}/windows/glog/raw_logging.h
    ${GLOG_P}/windows/glog/stl_logging.h
    ${GLOG_P}/windows/glog/log_severity.h
    ${GLOG_P}/windows/glog/logging.h
    ${GLOG_P}/windows/glog/vlog_is_on.h
  )
endif()


add_library(glog ${GLOG_FILES})
