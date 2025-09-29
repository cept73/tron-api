# Tron API - Обновление для PHP 8.4 и Laravel 12

## 🎉 Обновление завершено!

Проект успешно обновлен для работы с PHP 8.4 и Laravel 12. Все зависимости обновлены, код приведен в соответствие с современными стандартами PHP.

## ✅ Что было сделано

### 1. Обновлены зависимости в composer.json
- **PHP**: `>=8.1` (поддержка PHP 8.4)
- **Guzzle**: `^7.8|^8.0` (совместимость с Laravel 12)
- **Keccak**: `^1.1` (современная криптография)
- **phpseclib**: `^3.0` (современная криптография)
- **PHPUnit**: `^10.0` (современное тестирование)
- **PHPStan**: `^1.10` (статический анализ)

### 2. Исправлены сигнатуры методов
Все методы теперь имеют строгую типизацию:
```php
// Было:
public function setManager($providers) {
public function getEventResult($contractAddress, int $sinceTimestamp = 0, string $eventName = null, int $blockNumber = 0)

// Стало:
public function setManager($providers): void {
public function getEventResult($contractAddress, int $sinceTimestamp = 0, ?string $eventName = null, int $blockNumber = 0): array
```

### 3. Обновлены вызовы Guzzle
```php
// Было:
$options = [
    'headers'   => $this->headers,
    'body'      => json_encode($payload)
];

// Стало:
$options = [
    'headers'   => $this->headers,
    'json'      => $payload
];
```

### 4. Добавлен CI/CD
- GitHub Actions workflow для тестирования на PHP 8.1, 8.2, 8.3, 8.4
- Автоматический запуск тестов при push/PR
- Покрытие кода тестами
- Статический анализ с PHPStan

### 5. Обновлены тесты
- Совместимость с PHPUnit 10
- Строгая типизация тестовых методов
- Современные практики тестирования

## 🚀 Преимущества обновления

- ✅ **Поддержка PHP 8.4** - используйте новейшие возможности PHP
- ✅ **Совместимость с Laravel 12** - без конфликтов зависимостей
- ✅ **Современные зависимости** - безопасность и производительность
- ✅ **Улучшенная типизация** - меньше ошибок, лучшая читаемость
- ✅ **CI/CD автоматизация** - автоматическое тестирование
- ✅ **Статический анализ** - выявление потенциальных проблем

## 📦 Установка

```bash
# Клонирование репозитория
git clone <repository-url>
cd tron-api

# Установка зависимостей
composer install

# Запуск тестов
vendor/bin/phpunit

# Статический анализ
vendor/bin/phpstan analyse src --level=5
```

## 🧪 Тестирование

```bash
# Запуск всех тестов
vendor/bin/phpunit

# Запуск с покрытием
vendor/bin/phpunit --coverage-html coverage

# Статический анализ
vendor/bin/phpstan analyse src --level=5
```

## 🔧 Использование

```php
<?php

use IEXBase\TronAPI\Tron;
use IEXBase\TronAPI\Provider\HttpProvider;

// Создание экземпляра
$tron = new Tron(
    new HttpProvider('https://api.trongrid.io'),
    new HttpProvider('https://api.trongrid.io')
);

// Установка адреса
$tron->setAddress('TPL66VK2gCXNCD7EJg9pgJRfqcRazjhUZY');

// Получение баланса
$balance = $tron->getBalance();

// Создание TRC20 контракта
$contract = $tron->contract('TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t');

// Получение баланса токена
$tokenBalance = $contract->balanceOf();
```

## 📋 Совместимость

| Компонент | Версия | Статус |
|------------|--------|--------|
| PHP | 8.1+ | ✅ |
| PHP | 8.4 | ✅ |
| Laravel | 12 | ✅ |
| Guzzle | 7.8+ | ✅ |
| Guzzle | 8.0 | ✅ |
| PHPUnit | 10 | ✅ |

## 🐛 Исправленные проблемы

- Исправлены все Deprecation warnings для PHP 8.4
- Обновлены устаревшие зависимости
- Приведена в соответствие типизация методов
- Обновлены вызовы Guzzle для совместимости
- Исправлены тесты для PHPUnit 10

## 📚 Документация

- [UPGRADE.md](UPGRADE.md) - Подробное описание изменений
- [Исходный README](README.md) - Основная документация
- [Примеры](examples/) - Примеры использования

## 🤝 Вклад в проект

1. Форкните репозиторий
2. Создайте ветку для новой функции
3. Внесите изменения
4. Добавьте тесты
5. Создайте Pull Request

## 📄 Лицензия

MIT License - см. [LICENSE](LICENSE) файл.

---

**🎉 Проект готов к использованию с PHP 8.4 и Laravel 12!**
