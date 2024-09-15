# Coding cheatsheet

## Язык C

### Синтаксис

- Регистр (большие/маленькие буквы) имеет значение
- Каждое выражение должно заканчиваться `;`
- `//` начинает однострочный комментарий - текст после этого символа не влияет на работу программы, но позволяет программисту "объяснить", что она делает

### Функции

- Функция - участок кода, которым можно воспользоваться по имени

### Условия

```c
// Example

if(condition)
{
    // идем сюда, если условие (condition) выполняется
}
else
{
    // и сюда, если условие не выполняется
}
```

В качестве условия можно сравнивать значения:
- `>` больше
- `<` меньше
- `==` равно
- `!=` не равно
- `>=` больше либо равно
- `<=` меньше либо равно

```c
// Example

if(1 == 2);
if(4 < 5);
```

### Циклы

Циклы позволяют выполнять один и тот же код на повторе.

`for` выполняет код заданное количество раз

```c
// Example

for(int i=0; i<10; i++)
{
    Serial.println(i);
}
```


## Arduino

[Официальная документация](https://www.arduino.cc/reference/de/)

### Serial: передача данных между компьютером и Arduino

`Serial.begin(speed)` настроить скорость передачи данных

`Serial.print(value)` передать `value` на компьютер текстовым сообщением

`Serial.println(value)` то же самое, что `Serial.print`, но с переносом строки

```c
// Example

void setup(){
    Serial.begin(115200);
}

void loop(){
    Serial.print("I am ");
    Serial.print(10);
    Serial.println(" years old.");
}
```

### Работа с пинами

`pinMode(pin, mode)` переключить пин номер `pin` в режим `mode` (ввод `INPUT` или вывод `OUTPUT`)

`digitalWrite(pin, value)` вывести на пин номер `pin` значение `value` (`HIGH` или `LOW`)

```c
// Example

void setup(){
    pinMode(13, OUTPUT);
}

void loop(){
    digitalWrite(13, HIGH); // подать ток на пин 13
}
```

### Время

`delay(ms)` приостановить программу на `ms` миллисекунд (в 1 секунде 1000 миллисекунд)

### Звук

`tone(pin, frequency, duration)` воспроизводить на пине номер `pin` ноту частоты `frequency` в течение `duration` миллисекунд

[Таблица частот музыкальных нот](https://upload.wikimedia.org/wikipedia/commons/a/ad/Piano_key_frequencies.png)

```c
// Example

void loop(){
    tone(10, 440, 100);
}
```

## LOCO Board

### Создание проекта

- скопировать `modules.h` и `src` в папку проекта

- `#include "src/locoboard.h"`

### Пульт управления

`setup_ir()` настроить пульт управления (нужно сделать 1 раз в `setup`). Приемник должен быть подключен к пину 2.

`check_ir_button_pressed()` проверить, была ли нажата какая-то кнопка на пульте

`get_ir_button()` кнопка, которая была нажата на пульте. Доступные кнопки: `BTN_0`...`BTN_9`, `BTN_UP`, `BTN_DOWN`, `BTN_LEFT`, `BTN_RIGHT`, `BTN_OK`, `BTN_STAR`, `BTN_SHARP`.

```c
// Example

void setup() {
  setup_ir();
  Serial.begin(115200);
}

void loop() {
  if(check_ir_button_pressed())
  {
    if(get_ir_button() == BTN_0)
    {
      Serial.println(0);
    }
  }
}
```