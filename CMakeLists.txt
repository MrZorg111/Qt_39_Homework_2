cmake_minimum_required(VERSION 3.19)
project(Qt_39_Homework_2 LANGUAGES CXX)

find_package(Qt6 6.5 REQUIRED COMPONENTS Core Widgets)
find_package(Qt6 6.5 REQUIRED COMPONENTS Core5Compat)

qt_standard_project_setup()

qt_add_executable(Qt_39_Homework_2
    WIN32 MACOSX_BUNDLE
    main.cpp
    mainwindow.cpp
    mainwindow.h
    mainwindow.ui
)



target_link_libraries(Qt_39_Homework_2
    PRIVATE
        Qt::Core
        Qt::Widgets
        Qt6::Core5Compat
)

include(GNUInstallDirs)

install(TARGETS Qt_39_Homework_2
    BUNDLE  DESTINATION .
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
)

qt_generate_deploy_app_script(
    TARGET Qt_39_Homework_2
    OUTPUT_SCRIPT deploy_script
    NO_UNSUPPORTED_PLATFORM_ERROR
)
install(SCRIPT ${deploy_script})
