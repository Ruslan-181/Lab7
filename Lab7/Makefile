# Компілятор C
CC = gcc

# Прапорці компілятора
CFLAGS = -Wall

# Назви програми та статичної бібліотеки
PROGRAM = lab7_static
LIBRARY = libfunc.a

# Спочатку створюється програма
all: $(PROGRAM)

# Компіляція програми зі статичною бібліотекою
# Прапорець -lm потрібен для математичних функцій
$(PROGRAM): Lab7.o $(LIBRARY)
	$(CC) Lab7.o $(LIBRARY) -lm -o $(PROGRAM)

# Компіляція головного файлу
Lab7.o: Lab7.c Func.h
	$(CC) $(CFLAGS) -c $< -o $@

# Компіляція файлу бібліотеки
Func.o: Func.c Func.h
	$(CC) $(CFLAGS) -c $< -o $@

# Створення статичної бібліотеки
$(LIBRARY): Func.o
	ar rcs $@ $^

# Запуск програми
run: $(PROGRAM)
	./$(PROGRAM)

# Очищення папки від результатів компіляції
clean:
	rm -f $(PROGRAM) $(LIBRARY) Lab7.o Func.o output.txt data.bin