PROJECT(hello_world)
# PREJECT指令用法
# PROJECT(projectname [CXX] [C] [JAVA])
# 可以用这个指令定义工程的名称,并指定工程支持的语言,语言列表是可以忽略的,默认情况表示支持所有语言
# 这个指令还隐式定义了两个cmake变量 projectname_BINARY_DIR 和 projectname_SOURCE_DIR,因为采用的是内部编
#　译,两个变量目前指的是工作所在路径，如果是外部编译，两者所指代的内容会有所不同，但是如果改变工程名，
# 那么这两个变量也需要修改，那会很麻烦，所有，建议直接使用PROJECT_BINARY_DIR 和 PROJECT_SOURCE_DIR
# 外部编译时,PROJECT_BINATY_DIR指的是编译路径, PROJECT_SOURCE_DIR指工程路径

#source directory，源文件目录
AUX_SOURCE_DIRECTORY(src DIR_SRCS)

SET(TEST_HELLO ${DIR_SRCS})
#目前暂时先了解SET指令用来显式定义变量

MESSAGE(STATUS "This is Binary dir" ${hello_world_BINARY_DIR})
MESSAGE(STATUS "This is SOURCE dir" ${hello_world_SOURCE_DIR})
# MESSAGE用法
# MESSAGR([SEND_ERROR | STATUS | FATAL_ERROR] "message to display")
# SEND_ERROR : 产生错误,生成过程被跳过
# STATUS: 输出前缀为-的信息
# FATAL_ERROR: 立即终止所有cmake过程

# SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin) 
ADD_EXECUTABLE(${PROJECT_NAME} ${TEST_HELLO})
# ${}用来引用变量,
# 需要注意,指令大小写无关,参数和变量大小写相关,但是推荐使用大写指令
# ADD_EXECUTABLE 可以忽略source列表中的文件后缀,camke会在本目录自动查找,但是不推荐,万一存在main.

# ADD_TEST(NAME ${PROJECT_NAME} COMMAND ${PROJECT_NAME})



