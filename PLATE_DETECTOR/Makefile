# -isystem blabla: elimina i warnings per le librerie opencv
WFLAGS=-Wall -Wextra -isystem /usr/include/opencv

CFLAGS=-g $(shell pkg-config --cflags opencv) -I/usr/include/tesseract $(WFLAGS) -I/usr/include/opencv2
LIBS=$(shell pkg-config --libs opencv)
# -lcvaux -lhighgui
GCC=$(shell which g++)
SOURCES=$(shell ls *.cpp)
OBJECTS=$(SOURCES:.cpp=.o)
EXECUTABLE=plate
#V=1


# from Lauri Leukkunen's build system
ifdef V
  Q = 
  P = @printf "" # <- space before hash is important!!!
else
  P = @printf "[%s] $@\n" # <- space before hash is important!!!
  Q = @
endif


all: $(EXECUTABLE)


$(EXECUTABLE): $(OBJECTS)
	$(P)LD
	$(Q)$(GCC) ${OBJECTS} $(LIBS) $(CFLAGS) -o $@


%.o:: %.cpp
	$(P)CC
	$(Q)$(GCC) $(CFLAGS) -c -o $@ $<



clean:
	rm -f *.o $(EXECUTABLE)
