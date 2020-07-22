cmake_minimum_required(VERSION 3.10)
project(1ffmpegDemo)

set(CMAKE_CXX_STANDARD 11)

# 设置编译目标名称
SET(LINK_TARGETNAME 1ffmpegDemo)

# 表示生成的执行文件所在路径
SET(EXECUTABLE_OUTPUT_PATH "${CMAKE_SOURCE_DIR}/bin")

#设置头文件目录
INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/include)

#设置变量，表示所有的源文件
AUX_SOURCE_DIRECTORY(${CMAKE_SOURCE_DIR}/src LINK_SOURCEFILES)
# 设置链接库目录
LINK_DIRECTORIES(${CMAKE_SOURCE_DIR}/lib)
# 设置链接库名称
SET(LINK_LIB_LIST pthread  avformat avcodec avdevice avfilter  avutil swscale swresample )

#LINK_DIRECTORIES(usr/local/lib)

# add the executable
message(STATUS "add targent name:${LINK_TARGETNAME}")
ADD_EXECUTABLE(${LINK_TARGETNAME}  ${LINK_SOURCEFILES}
        )
# 依赖的库文件
TARGET_LINK_LIBRARIES(${LINK_TARGETNAME} ${LINK_LIB_LIST})


