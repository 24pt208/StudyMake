# Makefile для программы hello.cpp
# Вывод аргументов командной строки

.PHONY: all debug release clean help

# Определяем компилятор
CXX = g++

# Флаги компиляции
CXXFLAGS = -Wall -Wextra -pedantic
RELEASE_FLAGS = -O2 -DNDEBUG
DEBUG_FLAGS = -g -O0 -DDEBUG

# Имена исполняемых файлов
RELEASE_EXEC = hello
DEBUG_EXEC = hello-dbg

# Исходные файлы
SOURCES = hello.cpp

# Цели по умолчанию
all: release

# Release сборка
release: CXXFLAGS += $(RELEASE_FLAGS)
release: $(RELEASE_EXEC)

# Debug сборка
debug: CXXFLAGS += $(DEBUG_FLAGS)
debug: $(DEBUG_EXEC)

# Сборка release версии
$(RELEASE_EXEC): $(SOURCES)
	$(CXX) $(CXXFLAGS) $(SOURCES) -o $(RELEASE_EXEC)

# Сборка debug версии
$(DEBUG_EXEC): $(SOURCES)
	$(CXX) $(CXXFLAGS) $(SOURCES) -o $(DEBUG_EXEC)

# Очистка
clean:
	rm -f $(RELEASE_EXEC) $(DEBUG_EXEC)

# Помощь
help:
	@echo "Доступные цели:"
	@echo "  make all    - сборка release версии (по умолчанию)"
	@echo "  make release- сборка release версии"
	@echo "  make debug  - сборка debug версии"
	@echo "  make clean  - удаление скомпилированных файлов"
	@echo "  make help   - показать эту справку"
	@echo ""
	@echo "Примеры использования:"
	@echo "  ./hello"
	@echo "  ./hello arg1 arg2 arg3"
	@echo "  ./hello-dbg --test param"

# Тестовый запуск
test: release
	@echo "=== Тест без аргументов ==="
	./$(RELEASE_EXEC)
	@echo ""
	@echo "=== Тест с аргументами ==="
	./$(RELEASE_EXEC) first "second argument" third

# Информация о сборке
info:
	@echo "Компилятор: $(CXX)"
	@echo "Флаги release: $(RELEASE_FLAGS)"
	@echo "Флаги debug: $(DEBUG_FLAGS)"
	@echo "Исходные файлы: $(SOURCES)"
