find_package(PythonInterp REQUIRED)
set(destdir "$ENV{DESTDIR}")
find_file(destdir ${destdir} PATH ${CMAKE_BINARY_DIR})
if(destdir)
    set(PYINSTROOT "--root=${destdir}")
endif()
install(CODE "execute_process(COMMAND ${PYTHON_EXECUTABLE} setup.py install --prefix=${CMAKE_INSTALL_PREFIX} ${PYINSTROOT} WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})")
