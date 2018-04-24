OBJS=pngview.o
BIN=pngview

CFLAGS+=-Wall -g -O3 -I../common $(shell pkg-config libpng --cflags)
LDFLAGS+=-L/usr/lib/ -lbcm_host -lvchostif -lm $(shell pkg-config libpng --libs) -L../lib -lraspidmx

INCLUDES+=-I/usr/include -I/usr/include/interface/vcos/pthreads -I/usr/include/interface/vmcs_host/linux

all: $(BIN)

%.o: %.c
	@rm -f $@ 
	$(CC) $(CFLAGS) $(INCLUDES) -g -c $< -o $@ -Wno-deprecated-declarations

$(BIN): $(OBJS)
	$(CC) -o $@ -Wl,--whole-archive $(OBJS) $(LDFLAGS) -Wl,--no-whole-archive -rdynamic

clean:
	@rm -f $(OBJS)
	@rm -f $(BIN)
