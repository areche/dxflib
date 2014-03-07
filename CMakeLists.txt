cmake_minimum_required( VERSION 2.8 )

project( dxflib2_5 )

set( HEADERS
  src/dl_attributes.h
  src/dl_codes.h
  src/dl_creationadapter.h
  src/dl_creationinterface
  src/dl_dxf.h
  src/dl_entities.h
  src/dl_exception.h
  src/dl_writer.h
  src/dl_writer_ascii.h
)

set( SOURCES
  src/dl_dxf.cpp
  src/dl_writer_ascii.cpp
)

include_directories( ${PROJECT_SOURCE_DIR}/src )

if( WIN32 )
	add_library( ${PROJECT_NAME} STATIC ${HEADERS} ${SOURCES})
else()
	add_library( ${PROJECT_NAME} SHARED ${HEADERS} ${SOURCES})
endif()

install(FILES ${HEADERS} DESTINATION include)

install(TARGETS ${PROJECT_NAME} 
  RUNTIME DESTINATION bin COMPONENT applications
  LIBRARY DESTINATION lib COMPONENT libraries
  ARCHIVE DESTINATION lib COMPONENT headers
)

#target_link_libraries( ${PROJECT_NAME} )

#add_subdirectory( test )
