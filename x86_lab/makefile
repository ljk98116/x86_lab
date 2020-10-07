OBJCC = as
LINKCC = ld
APPFILE = obj/myapp

SRC = $(wildcard src/*.S)
OBJ = $(SRC:src/%.S=obj/%.o)

.PHONY:all
all:
	mkdir obj
	make $(APPFILE)

$(APPFILE): $(OBJ)
	$(LINKCC) -o $@ $^

obj/%.o: src/%.S
	$(OBJCC) -o $@ $^ --gstabs

.PHONY:clean
clean:
	rm -rf obj

.PHONY:objdump
objdump:
	objdump -D $(OBJ)

.PHONY:run
run:
	make all
	./$(APPFILE)
	
.PHONY:debug
debug:
	gdb $(APPFILE)
