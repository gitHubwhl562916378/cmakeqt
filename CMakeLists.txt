cmake_minimum_required(VERSION 3.0.0)

project(cmakeqt)

set(Qt5_DIR /home/whl/Qt5.9.3/5.9.3/gcc_64/lib/cmake/Qt5)
set(CMAKE_AUTOMOC ON) #自动生成moc文件
set(CMAKE_AUTORCC ON) #自动处理rcc文件
set(CMAKE_AUTOUIC ON) #自动处理uic
#查找当前文件夹中的所有源代码文件，也可以通过Set命令将所有文件设置为一个变量
FILE(GLOB SRC_FILES "./*.cpp") 
#同理，查找当前文件夹中所有的头文件
FILE(GLOB HEAD_FILES "./*.h") 
#同理，查找当前文件夹中所有的ui文件
FILE(GLOB UI_FILES "./*.ui")

#通过Ui文件生成对应的头文件，一定要添加
# qt5_wrap_ui(WRAP_FILES ${UI_FILES})
 
#添加资源文件
# set(RCC_FILES rcc.qrc)

find_package(Qt5 REQUIRED Widgets Core Gui)

add_executable(${PROJECT_NAME} ${SRC_FILES} ${HEAD_FILES} ${RCC_FILES} ${WRAP_FILES})
target_link_libraries(${PROJECT_NAME} Qt5::Widgets Qt5::Core Qt5::Gui)
