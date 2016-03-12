#
# project: fips-docopt
#
if (NOT FIPS_IMPORT)
    cmake_minimum_required(VERSION 2.8)
    get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
    include("${FIPS_ROOT_DIR}/cmake/fips.cmake")
    fips_setup()
    fips_project(fips-docopt)
endif()

message(STATUS "docopt requires EXCEPTIONS and RTTI enabled.")
set(FIPS_EXCEPTIONS ON)
set(FIPS_RTTI ON)

fips_begin_lib(docopt)
	fips_include_directories(docopt.cpp)
	fips_files_ex(docopt.cpp/ docopt*.* GROUP "docopt.cpp")
fips_end_lib()

fips_begin_app(naval_fate cmdline)
    fips_src(docopt.cpp/examples)
    fips_deps(docopt)
fips_end_app()

if (CMAKE_COMPILER_IS_GNUCXX)
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-unknown-pragmas")	# Code uses #pragma mark
elseif (FIPS_WINDOWS)
	set_target_properties(docopt PROPERTIES COMPILE_FLAGS "/wd4068") # pragma mark
endif()

if (NOT FIPS_IMPORT)
    fips_finish()
endif()