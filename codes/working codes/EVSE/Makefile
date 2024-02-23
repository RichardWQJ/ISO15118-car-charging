TARGET=EVSE
SOURCE = $(wildcard *.c)
OBJS = $(patsubst %.c,%.o,$(SOURCE))
	
CROSS_COMPILE =
CXX = gcc
 
CFLAGS += --static
CLFAGS += -Wall 
LDFLAGS += -lm
	
all:$(TARGET)
$(TARGET):$(OBJS)
	$(CROSS_COMPILE)$(CXX) -Wall $(CFLAGS) -o $@ $^
 
.PHONY:clean
clean:
	rm -f *.o *.d $(TARGET)
 
include $(SOURCE:.c=.d)	
	
%.o:%.c
	$(CROSS_COMPILE)$(CXX) -Wall $(CFLAGS) -c $< -o $@
 
%.d: %.c
	@set -e; rm -f $@; \
	$(CXX) -MM $(CFLAGS) $< > $@.$$$$; \
	sed 's,\($*\)\.o[ :]*,\1.o $@ : ,g' < $@.$$$$ > $@; \
	rm -f $@.$$$$
