# Компілятор C
CC = gcc

# Прапорці компілятора
CFLAGS = -Wall
PICFLAGS = -fPIC

# Назви програми та динамічної бібліотеки
PROGRAM = lab7_dynamic
LIBRARY = libfunc.so

# Спочатку створюється програма
all: $(PROGRAM)

# Компіляція програми з динамічною бібліотекою
# -L. означає шукати бібліотеку в поточній папці
# -lfunc підключає файл libfunc.so
$(PROGRAM): Lab7.o $(LIBRARY)
	$(CC) Lab7.o -L. -lfunc -lm -Wl,-rpath,. -o $(PROGRAM)

# Компіляція головного файлу
Lab7.o: Lab7.c Func.h
	$(CC) $(CFLAGS) -c $< -o $@

# Компіляція бібліотеки
# -fPIC потрібен для створення динамічної бібліотеки
Func.o: Func.c Func.h
	$(CC) $(CFLAGS) $(PICFLAGS) -c $< -o $@

# Створення динамічної бібліотеки libfunc.so
# Ключ -shared створює файл .so замість звичайної програми
$(LIBRARY): Func.o
	$(CC) -shared -o $@ $^

# Запуск програми
run: $(PROGRAM)
	./$(PROGRAM)

# Очищення папки від результатів компіляції
clean:
	rm -f $(PROGRAM) $(LIBRARY) Lab7.o Func.o output.txt data.bin
