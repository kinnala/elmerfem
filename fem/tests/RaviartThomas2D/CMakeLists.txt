INCLUDE(test_macros)
INCLUDE_DIRECTORIES(${CMAKE_BINARY_DIR}/fem/src)

CONFIGURE_FILE( RT.sif RT.sif COPYONLY)
ADD_ELMERTEST_MODULE(RaviartThomas2D Source Source.F90)
ADD_ELMERTEST_MODULE(RaviartThomas2D ComputeError ComputeError.F90)

file(COPY ELMERSOLVER_STARTINFO square Source.F90 ComputeError.F90 DESTINATION "${CMAKE_CURRENT_BINARY_DIR}/")

ADD_ELMER_TEST(RaviartThomas2D LABELS quick vector_element)
