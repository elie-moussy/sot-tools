
# Copyright 2012, CNRS
# Author: Florent Lamiraux
#

SET (LIBRARY_NAME ${PROJECT_NAME})

ADD_LIBRARY (${LIBRARY_NAME} SHARED
  cubic-interpolation.cc
  cubic-interpolation.hh
  cubic-interpolation-se3.cc
  cubic-interpolation-se3.hh
  oscillator.cc
  seqplay.cc
  seqplay.hh
  )

PKG_CONFIG_USE_DEPENDENCY (${LIBRARY_NAME} sot-core)
DYNAMIC_GRAPH_PYTHON_MODULE ("sot/tools" ${LIBRARY_NAME} wrap)
INSTALL (TARGETS ${LIBRARY_NAME} DESTINATION ${CMAKE_INSTALL_LIBDIR})

INSTALL(FILES
  ${CMAKE_CURRENT_SOURCE_DIR}/dynamic_graph/sot/tools/se3.py
  ${CMAKE_CURRENT_SOURCE_DIR}/dynamic_graph/sot/tools/quaternion.py
  DESTINATION ${PYTHON_SITELIB}/dynamic_graph/sot/tools
  )
