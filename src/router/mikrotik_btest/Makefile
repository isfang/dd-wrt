
CFLAGS = $(COPTS) $(MIPS16_OPT) -ffunction-sections -fdata-sections -DNEED_PRINTF
LDFLAGS = $(COPTS) $(MIPS16_OPT) -Wl,--gc-sections
LDLIBS += -lpthread -lrt

all: mikrotik_btest btest
	
mikrotik_btest: main.o parse_opt.o tcptest_thread.o tcptest.o messages.o md5.o utils.o
	$(CC) $(LDFLAGS) -o $@ $^ $(LDLIBS)
	
btest: btest.o timing_mach.c
	$(CC) $(LDFLAGS) -o $@ $^ -lpthread

main.o: main.c
	$(CC) $(CFLAGS) -c -o $@ $<

parse_opt.o: parse_opt.c
	$(CC) $(CFLAGS) -c -o $@ $<

tcptest.o: tcptest.c
	$(CC) $(CFLAGS) -c -o $@ $<

tcptest_thread.o: tcptest_thread.c
	$(CC) $(CFLAGS) -c -o $@ $<

messages.o: messages.c
	$(CC) $(CFLAGS) -c -o $@ $<

md5.o: md5.c
	$(CC) $(CFLAGS) -c -o $@ $<
	
utils.o: utils.c
	$(CC) $(CFLAGS) -c -o $@ $<
	
clean: 
	rm -f mikrotik_btest *.o

install:
	install -D mikrotik_btest $(INSTALLDIR)/usr/sbin/mikrotik_btest
	install -D btest $(INSTALLDIR)/usr/sbin/btest