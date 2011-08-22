cmake_minimum_required( VERSION 2.8 )

project( LargeImageDisplay )

find_package(ITK REQUIRED)
include(${ITK_USE_FILE})

find_package(VTK REQUIRED)
include(${VTK_USE_FILE})

include(CTest)
include(CPack)

set( CMAKE_MODULE_PATH
  "${PROJECT_SOURCE_DIR}/CMake"
  ${CMAKE_MODULE_PATH}
)

include_directories( BEFORE
  ${PROJECT_SOURCE_DIR}/include
)

add_executable( ImageDisplay ImageDisplay.cxx vtkInteractorStyleImageCursor.cxx itkReaderStreamingWatcher.h )
target_link_libraries( ImageDisplay ${ITK_LIBRARIES}
  vtkRendering vtkIO vtkHybrid )

add_executable( ImageSurfaceDisplay ImageSurfaceDisplay.cxx itkReaderStreamingWatcher.h )
target_link_libraries( ImageSurfaceDisplay ${ITK_LIBRARIES}
  vtkRendering vtkIO vtkHybrid )
