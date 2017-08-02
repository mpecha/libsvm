cmake_minimum_required(VERSION 3.7)
project(LIBSVM)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/lib)

set(SOURCES_SVM svm.cpp svm.h)
set(SOURCES_PREDICT svm-predict.c)
set(SOURCES_SCALE svm-scale.c)
set(SOUCES_TRAIN svm-train.c)

add_library(svm SHARED ${SOURCES_SVM})
add_executable(svm-predict ${SOURCES_PREDICT} ${SOURCES_SVM})
target_link_libraries(svm-predict LINK_PUBLIC svm)
add_executable(svm-scale ${SOURCES_SCALE} ${SOURCES_SVM})
target_link_libraries(svm-predict LINK_PUBLIC svm)
add_executable(svm-train ${SOUCES_TRAIN} ${SOURCES_SVM})
target_link_libraries(svm-predict LINK_PUBLIC svm)