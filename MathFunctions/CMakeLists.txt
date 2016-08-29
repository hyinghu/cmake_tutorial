add_library(MathFunctions SHARED mysqrt.cpp)

install (TARGETS MathFunctions DESTINATION lib)
install (FILES MathFunctions.h DESTINATION include)
