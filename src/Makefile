CFLAGS = -g -O2 -Wall -lpthread
LIB = -lrt
OBJS = slog.o

LIBINSTALL = /usr/local/lib
HEADINSTALL = /usr/local/include

.c.o:
	$(CC) $(CFLAGS) -c $< $(LIB)

libslog.a: $(OBJS)
	$(AR) rcs libslog.a $(OBJS)
	@echo [-] Syncing static library
	sync

install:
	@test -d $(LIBINSTALL) || mkdir $(LIBINSTALL)
	@test -d $(HEADINSTALL) || mkdir $(HEADINSTALL)
	@install -m 0664 libslog.a $(LIBINSTALL)/
	@install -m 0664 slog.h $(HEADINSTALL)/
	@echo [-] Done

slog.o: slog.h

.PHONY: clean
clean:
	$(RM) libslog.a $(OBJS)
