# Утилиты для функций
<br>
<strong>Функция _error-type-scss()</strong>
<p>Для чего нужна данная функция?</p>
<p>Выводить вид ошибки в консоль;</p>
<ul>
    <li>'warn' - возвращает ошибку @warn</li>
    <li>'error' -  возвращает ошибку @error</li>
    <li>'not-error' - не выводить ошибку в консоль</li>
</ul>
<p>Не имеет значений "по умолчанию"</p>
<pre><code>Принимает значения:
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
</code></pre>
<br>
<br>
<br>
<strong>Функция _return-type-of-value()</strong>
<p>Для чего нужна данная функция? <br>
Для возвращения типа значений при ошибках в функциях;</p>
<p>по умолчанию = null</p>
<pre><code>Принимает значения:
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
</code></pre>