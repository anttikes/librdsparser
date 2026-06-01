cmake_minimum_required(VERSION 3.10)

if (RDSPARSER_BUILD_STATIC)
    add_library(rdsparser STATIC)    
else()
    add_library(rdsparser SHARED)
endif()

target_sources(rdsparser PRIVATE
        af.c
        buffer.c
        country.c
        ct.c
        ecc.c
        group.c
        group0.c
        group1.c
        group2.c
        group4.c
        group10.c
        group15.c
        lps.c
        parser.c
        pty.c
        rdsparser.c
        string.c
        utils.c
)

target_include_directories(rdsparser PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

if (RDSPARSER_DISABLE_HEAP)
    target_compile_definitions(rdsparser PUBLIC RDSPARSER_DISABLE_HEAP)
endif()

if (RDSPARSER_DISABLE_UNICODE)
    target_compile_definitions(rdsparser PUBLIC RDSPARSER_DISABLE_UNICODE)
endif()

#add_library(rdsparser SHARED ${SOURCE_FILES})
#set_target_properties(rdsparser PROPERTIES PUBLIC_HEADER librdsparser.h)

#add_library(rdsparser_static STATIC ${SOURCE_FILES})
#set_target_properties(rdsparser_static PROPERTIES PUBLIC_HEADER librdsparser.h)

#if(RDSPARSER_DISABLE_HEAP)
    #set_target_properties(rdsparser PROPERTIES PUBLIC_HEADER librdsparser_private.h)
    #set_target_properties(rdsparser_static PROPERTIES PUBLIC_HEADER librdsparser_private.h)
#endif()
