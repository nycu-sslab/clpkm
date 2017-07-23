CXX         = g++
LLVM_CONFIG = llvm-config

CXXFLAGS = -Wall -Wextra -pedantic -fstack-protector-strong -g3 \
           # -O2 -ftree-vectorize -fno-plt -flto
LDFLAGS  = -Wl,-O1,--sort-common,--as-needed,-z,relro,-z,now # -s
LIBS     = -lyaml-cpp -lOpenCL -ldl

TARGET   := libclpkm.so
SRCS     := $(wildcard *.cpp)
OBJS     := ${SRCS:%.cpp=%.o}

all: $(TARGET)

$(TARGET): $(OBJS)
	$(CXX) $(CXXFLAGS) $(LDFLAGS) -std=c++17 -DHAVE_YAMLCPP -shared $^ -o $@ $(LIBS)

%.o: %.cpp
	$(CXX) $(CXXFLAGS) -std=c++17 -DHAVE_YAMLCPP -fPIC $< -c -o $@

.PHONY: clean

clean:
	$(RM) $(TARGET) *.o