BUILD_DIR = ./build
CC = gcc
LD = ld
LIB = -I .
CFLAGS = $(LIB) -c
LDFLAGS = -e main 

OBJS = $(BUILD_DIR)/main.o $(BUILD_DIR)/add_word.o $(BUILD_DIR)/dump_word.o \
       $(BUILD_DIR)/finalize.o $(BUILD_DIR)/initialize.o $(BUILD_DIR)/get_word.o

$(BUILD_DIR)/main.o: main.c get_word.h word_manage.h word_manage_p.h 
	$(CC) $(CFLAGS) $< -o $@

$(BUILD_DIR)/add_word.o: word_manage_p.h
	$(CC) $(CFLAGS) $< -o $@
	
$(BUILD_DIR)/dump_word.o: word_manage_p.h
	$(CC) $(CFLAGS) $< -o $@
	
$(BUILD_DIR)/finalize.o: word_manage_p.h
	$(CC) $(CFLAGS) $< -o $@
	
$(BUILD_DIR)/initialize.o: word_manage_p.h
	$(CC) $(CFLAGS) $< -o $@
	
$(BUILD_DIR)/get_word.o: get_word.h
	$(CC) $(CFLAGS) $< -o $@
	


##############    链接所有目标文件    #############
$(BUILD_DIR)/output: $(OBJS)
	$(CC) $^ -o $@
# $(LD) $(LDFLAGS) $^ -o $@

.PHONY : mk_dir clean all

mk_dir:
	if [[ ! -d $(BUILD_DIR) ]];then mkdir $(BUILD_DIR);fi

clean:
	cd $(BUILD_DIR) && rm -f ./*

build: $(BUILD_DIR)/output

start:
	$(BUILD_DIR)/output

all: mk_dir build start
