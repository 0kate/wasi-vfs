-include ../tools.mk

objs = $(TMPDIR)/main.c.o

check: $(objs)
	$(CC) $(LDFLAGS) $(objs) $(LIB_WASI_VFS) -o $(TMPDIR)/main.wasm
	$(WASI_RUN) --mapdir /mnt::./mnt $(TMPDIR)/main.wasm
	$(WASI_VFS_CLI) pack $(TMPDIR)/main.wasm --mapdir /mnt::./mnt -o $(TMPDIR)/main.packed.wasm
	$(WASI_RUN) $(TMPDIR)/main.packed.wasm

clean:
	rm -rf $(PROG) $(objs)
