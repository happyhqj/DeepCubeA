CXX=g++
OPENMP_FLAGS=$(shell printf 'int main(){return 0;}\n' | $(CXX) -x c++ -fopenmp - >/dev/null 2>&1 && printf -- '-fopenmp')
CXXFLAGS=-Wall -Wextra -Wpedantic -Wconversion -std=c++11 -DNDEBUG -O3 -pthread

ifeq ($(OPENMP_FLAGS),)
CXXFLAGS += -Wno-unknown-pragmas
else
CXXFLAGS += $(OPENMP_FLAGS)
endif

all: parallel_weighted_astar

parallel_weighted_astar: *.cpp
	$(CXX) $(CXXFLAGS) *.cpp -o parallel_weighted_astar

clean:
	rm -fr *.o parallel_weighted_astar
