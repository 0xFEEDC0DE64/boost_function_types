# Copyright 2019 Mike Dev
# Distributed under the Boost Software License, Version 1.0.
# See accompanying file LICENSE_1_0.txt or copy at https://www.boost.org/LICENSE_1_0.txt

if(NOT DEFINED IDF_TARGET)

cmake_minimum_required( VERSION 3.5...3.20 )
project( boost_function_types VERSION "${BOOST_SUPERPROJECT_VERSION}" LANGUAGES CXX )

add_library( boost_function_types INTERFACE )
add_library( Boost::function_types ALIAS boost_function_types )

target_include_directories( boost_function_types INTERFACE include )

target_link_libraries( boost_function_types
    INTERFACE
        Boost::config
        Boost::core
        Boost::detail
        Boost::mpl
        Boost::preprocessor
        Boost::type_traits
)

else()

FILE(GLOB_RECURSE headers include/*.h include/*.hpp)

idf_component_register(
    SRCS
        ${headers}
    INCLUDE_DIRS
        include
    REQUIRES
        boost_config
        boost_core
        boost_detail
        boost_mpl
        boost_preprocessor
        boost_type_traits
)

endif()
