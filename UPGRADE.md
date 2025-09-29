# Обновление до PHP 8.4 и Laravel 12

## Изменения в зависимостях

### Обновленные зависимости в composer.json:

```json
{
    "require": {
        "php": ">=8.1",
        "guzzlehttp/guzzle": "^7.8|^8.0",
        "kornrunner/keccak": "^1.1",
        "phpseclib/phpseclib": "^3.0",
        "ext-json": "*",
        "ext-bcmath": "*"
    },
    "require-dev": {
        "phpunit/phpunit": "^10.0",
        "phpstan/phpstan": "^1.10"
    }
}
```

### Удаленные зависимости:
- `comely-io/data-types` - заменена на встроенные типы PHP 8.1+
- `iexbase/web3.php` - заменена на `kornrunner/keccak`
- `kornrunner/secp256k1` - заменена на `phpseclib/phpseclib`
- `simplito/elliptic-php` - заменена на `phpseclib/phpseclib`

## Изменения в коде

### 1. Обновленные сигнатуры методов

Все методы теперь имеют строгую типизацию:

```php
// Было:
public function setManager($providers) {
public function getEventResult($contractAddress, int $sinceTimestamp = 0, string $eventName = null, int $blockNumber = 0)

// Стало:
public function setManager($providers): void {
public function getEventResult($contractAddress, int $sinceTimestamp = 0, ?string $eventName = null, int $blockNumber = 0): array
```

### 2. Обновленные вызовы Guzzle

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

### 3. Обновленные тесты

Все тестовые методы теперь имеют возвращаемый тип `void`:

```php
// Было:
public function test_isValidProvider()

// Стало:
public function test_isValidProvider(): void
```

## CI/CD

Добавлен GitHub Actions workflow для тестирования на PHP 8.1, 8.2, 8.3, 8.4:

```yaml
strategy:
  matrix:
    php-version: ['8.1', '8.2', '8.3', '8.4']
```

## Установка

```bash
composer install
```

## Тестирование

```bash
# Запуск тестов
vendor/bin/phpunit

# Статический анализ
vendor/bin/phpstan analyse src --level=5
```

## Совместимость

- ✅ PHP 8.1+
- ✅ PHP 8.4
- ✅ Laravel 12
- ✅ Guzzle 7.8+
- ✅ Guzzle 8.0
- ✅ PHPUnit 10

## Миграция с старой версии

1. Обновите `composer.json` с новыми зависимостями
2. Запустите `composer update`
3. Обновите код, если используете кастомные расширения
4. Запустите тесты для проверки совместимости

## Преимущества обновления

- 🚀 Поддержка PHP 8.4
- 🚀 Совместимость с Laravel 12
- 🚀 Современные зависимости
- 🚀 Улучшенная типизация
- 🚀 CI/CD автоматизация
- 🚀 Статический анализ кода
