# Утилиты для функций

## Функция _error-type-scss()
Для чего нужна данная функция? <br />
Выводить вид ошибки в консоль.

* 'warn' - возвращает @warn
* 'error' -  возвращает @error
* 'not-error' - не выводить ошибку в консоль

Не имеет значений "по умолчанию"

```scss
Принимает значения:
    _error-type-scss(
        1. value: 'warn', 'error', 'not-error',
        2. return: что возвращать?,
        3. message: Текст ошибки
    )

Пример использования:
    _error-type-scss(
        $error-type (или 'warn', 'error', 'not-error'),
        false,
        'Accepts type of values: #{$type-of-value}'
    ); 

Ошибки:
    При не верном вводе $value, возвращает ошибку.
```
## Функция _return-type-of-value()

Для чего нужна данная функция? <br />
Для возвращения типа значений при ошибках в функциях;
по умолчанию = null>

```scss
# Принимает значения:
    _error-type-scss(
        Значение должно быть строкой
        1. value:   'null' - возвращает: null;
                    'list' - возвращает пустой лист: ();
                    'string' - возвращает пустую строку: '';
                    'false' - возвращает: false;
                    'true' - возвращает: true;
    )
    Пример использования:
    @function test($value, $return-type-of-value) {
        @if type-of($value) == number {
            @return $value;
        } @else {
            @return _return-type-of-value($return-type-of-value);
        }
    }
    @debug type-of(test(string, 'null')); // null - null
    @debug type-of(test(string, 'list')); // () - list
    @debug type-of(test(string, 'string')); // '' - string
    @debug type-of(test(string, 'false')); // false - boll
    @debug type-of(test(string, 'true')); // true - boll
    @debug type-of(test(string, true)); // Ошибка, значение должно быть строкой

    Ошибки:
    При не верном вводе $value, возвращает ошибку.
```
