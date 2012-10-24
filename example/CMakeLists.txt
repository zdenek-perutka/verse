
# Cmake file for example of verse client

if (CMAKE_COMPILER_IS_GNUCC)
	set (CMAKE_C_FLAGS "-D_REETRANT -ggdb -Wall -Wextra -pedantic -O0")
endif (CMAKE_COMPILER_IS_GNUCC)

# Source code
set (verse_client_src verse_client.c)

# Directory with .h files
include_directories (../include)
include_directories (${OPENSSL_INCLUDE_DIR})

# Define executable
add_executable (verse_client ${verse_client_src})
add_dependencies (verse_client verse_shared_lib)
target_link_libraries (verse_client
		verse_shared_lib
		${CMAKE_THREAD_LIBS_INIT}
		${OPENSSL_LIBRARIES})