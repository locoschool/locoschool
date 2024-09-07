# Coding cheatsheet

## Язык C

### Синтаксис

- Регистр (большие/маленькие буквы) имеет значение
- Каждое выражение должно заканчиваться `;`
- `//` начинает однострочный комментарий - текст после этого символа не влияет на работу программы, но позволяет программисту "объяснить", что она делает

### Функции

- Функция - участок кода, которым можно воспользоваться по имени

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