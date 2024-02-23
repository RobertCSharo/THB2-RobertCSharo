# BTHome THB1, THB2, BTH01, TH05(HW: v1.3..1.6), TH05F 
Custom firmware for Tuya devices on the PHY622x2 chipset
| [THB1](https://pvvx.github.io/THB1) | [THB2](https://pvvx.github.io/THB2) | [BTH01](https://pvvx.github.io/BTH01/) | [TH05_V1.3](https://pvvx.github.io/TH05-v1.3) | [TH05_V1.4](https://pvvx.github.io/TH-05) | [TH05F](https://pvvx.github.io/TH05F) |
|:---:|:---:|:---:|:---:|:---:|:---:|
| ![THB1](https://pvvx.github.io/THB1/img/THB1.jpg) | ![THB2](https://pvvx.github.io/THB2/img/THB2.jpg) | ![BTH01](https://pvvx.github.io/BTH01/img/BTH01.jpg) | ![TH05V1.3](https://pvvx.github.io/TH05-v1.3/img/TH05-V1.3.jpg) | ![TH05V1.4](https://pvvx.github.io/TH-05/img/TH05V14.jpg) | ![TH05F](https://pvvx.github.io/TH05F/img/TH05F.jpg)

* Программа для настройки и BLE OTA [PHY62x2BTHome.html](https://pvvx.github.io/THB2/web/PHY62x2BTHome.html)

## Прошивки Boot и APP:

* Прошивка [Boot](https://github.com/pvvx/THB2/issues/10) имеет минимум функций. Boot используются только для выполнения OTA - для загрузки полнофункциональной версии APP (Application - файлы *.bin).
* Внешне отличить тип устройства возможно по символу смайлика на экране.

| Устройство | Файл Boot | Файл OTA | Маркировка на печатной плате |
|:---:|:---:|:---:|
| [THB1](https://pvvx.github.io/THB1) | BOOT_THB1_v14.hex | THB1_v14.bin | нет |
| [THB2](https://pvvx.github.io/THB2) | BOOT_THB2_v14.hex | THB2_v14.bin | нет |
| [BTH01](https://pvvx.github.io/BTH01) | BOOT_BTH01_v14.hex | BTH01_v14.bin | нет |
| [TH05_V1.4](https://pvvx.github.io/TH-05) | BOOT_TH05_v14.hex | TH05_v1.4.bin | TH05_V1.4, TH05_V1.5, TH05_V1.6 с чипом BL55028 |
| [TH05_V1.3](https://pvvx.github.io/TH05-v1.3) | BOOT_TH05D_v14.hex | TH05D_v14.bin | RSH-TH05-V1.3 с чипом BL55072 |
| [TH05F](https://pvvx.github.io/TH05F) | BOOT_TH05F_v14.hex | TH05F_v14.bin | TH05Y_V1.1, TH05Y_V1.2 с чипом QD01 2332 NT |

## Основные характеристики:

! _При настройках по умолчанию_ !

* Интервал BLE рекламы в формате [BTHome v2](https://bthome.io) равен 5 секундам.
* Опрос датчика влажности и температуры производится каждый второй интервал BLE рекламы - период 10 секунд.
* Измерение напряжения батареи происходит каждую минуту.
* Кнопка используется для быстрого подключения к старым BT-адаптерам. Нажатие кнопки переключает интервал BLE рекламы на более короткий период (1562.5 мс). Действие продолжится 60 секунд, затем интервал восстановится на установленный в настройках.
* Измеренное среднее потребление от источника в 3.3В при сканировании термометров THB2 и BTH01 в пассивном режиме составляет до 8 мкА. Для TH05_V1.4 среднее потребление около 23 мкА - [таков ток установленных компонентов](https://github.com/pvvx/THB2/issues/8#issuecomment-1908982171).
* Запись итории каждые 30 минут
* Интервал соединения с учетом Connect Latency - 900 мс
* Поддерживаемые сенсоры температуры и влажности: AHT30, CHT8305, CHT8215, CHT8310
* Обработка входного контакта со счетчиком для передаваемых событий [Open/Close](https://github.com/pvvx/THB2/issues/10#issuecomment-1935169274)
* Обработка выходного контакта переключаемого по устанавливаемой температуре и/или влажности с гистерезисом

## История версий:

| N | Описание |
|---|--- |
| 1.0 | Первая релизная версия |
| 1.1 | Добавлен триггер - вывод TX2 срабатывающий по установленным значениям температуры и/или влажности с гистерезисами. Передача состояния вывода RX2 при connect. Для термометров с экраном добавлен показ смайлика с "комфортом". Дополнены: изменение имени и MAC устройства. |
| 1.2 | Обработка и передача событий open/close со счетчиком с вывода маркированного "RX2" (для THB2 - "RX1"). |
| 1.3 | Добавлен THB1 и TH05V1.3. Следующий этап уменьшения потребления для версий с LCD дисплеем и опция отключения дисплея. |
| 1.4 | Стабилизация соединения для всех вариантов устройств. Добавлен [TH05F](https://pvvx.github.io/TH05F). Коррекция хода RTC. |

## Прошивка:

Прошить устройство програмой Boot-OTA возможно через USB-COM адаптер с выходами на 3.3В:

1. Соединить GND, TX, RX, RTS–RESET, VCC (+3.3B).

| Адаптер | Устройство |
|---|---|
| GND | -Vbat |
| +3.3В | +Vbat |
| TX | RX1 |
| RX | TX1 |
| RTS | RESET |

Название контактов на устройстве смотреть в описании по ссылкам: [THB1](https://pvvx.github.io/THB1), [THB2](https://pvvx.github.io/THB2), [BTH01](https://pvvx.github.io/BTH01/), [TH05_V1.3](https://pvvx.github.io/TH05-v1.3), [TH05_V1.4](https://pvvx.github.io/TH-05)

2. Запустить:
```
python3 rdwr_phy62x2.py -p COM11 -e -r wh BOOT_xxx_vxx.hex
```
3. Прошивка Boot-OTA завершена. Устройство работает.
4. Далее загружаем полную версию по OTA в [PHY62x2BTHome.html](https://pvvx.github.io/THB2/web/PHY62x2BTHome.html).

Дополнительно:

* Для предварительного стирания всей Flash используйте опцию `-a`.

* Для предварительного стирания рабочей области Flash используйте опцию `-e`.

## Сохранение оригинальной прошивки.

1. Соединить GND, TX, RX, RTS–RESET, VCC (+3.3B).
2. Запустить:
```
python3 rdwr_phy62x2.py -p COM11 -r rc 0x11000000 0x80000 ff_thb2.bin
```
3. Полученный файл ff_thb2.bin сохранить.

## Восстановление оригинальной прошивки.

1. Взять сохраненный файл ff_thb2.bin оригинальной прошивки.
2. Соединить GND, TX, RX, RTS–RESET, VCC (+3.3B).
3. Запустить:
```
python3 rdwr_phy62x2.py -p COM11 -b 1000000 -r we 0 ff_thb2.bin
```
Не все адаптеры USB-COM поддерживают 1Mbit. Тогда удалите опцию `-b 1000000` или выберите другой Baud rate.

4. Прошивка зашита. Устройство работает.

## Распределение Flash 512 килобайт

| Адрес | Описание | Размер |
|---|---|---|
| 0x00000 | Используется ROM | 8 килобайт |
| 0x02000 | Boot Info для ROM | 4 килобайта |
| 0x03000 | FW Boot с функцией OTA | 52 килобайта |
| 0x10000 | FW APP | 128 килобайт |
| 0x30000 | Запись истории | 304 килобайт |
| 0x7C000 | Сохранение настроек (EEP) | 16 килобайт |

## FW Boot и OTA

* `FW Boot` имеет функцию OTA, но не имеет функции записи истории и прочих дополнений. Служит для обработки OTA при любых неудачных или неправильных обновлениях.

* `FW APP` не имеет функции OTA, для OTA перезагружается в `FW Boot`. Имеет дополнительные функции и расширения.

Поддерживаемые функции и сервисы описываются включенными битами в 32-х битном поле `dev_id.services`.

`FW Boot` запускается по старту, и если не нажата кнопка, проверяет есть или нет запись `FW APP`. Если есть – запускает `FW APP`. Если кнопка при старте нажата - запускается `FW Boot`. 

При соединении указывается:

_Software:_ **V**x.x - значит работает `FW APP`
_Software:_ **B**x.x - значит работает `FW Boot`

На термометрах с экраном, если не включено отображение времени, при первом старте показывает:

* "Bot 12" - работает Boot версия 1.2
* "APP 12" - работает APP версия 1.2  

Принудительно перезагрузиться в `FW Boot` из `FW APP` возможно двумя способами:

1.	Отключить питание и удерживая кнопку включить питание.
2.	Подать команду `7233` в меню `Service` программы PHY62x2BTHome.html и отключить соединение.

Полная перезагрузка - Подать команду `7201` в меню `Service` программы PHY62x2BTHome.html и отключить соединение.

Через USB-UART адаптер App можно записать сразу после boot. Пример:

```
python3 rdwr_phy62x2.py -p COM11 -e wh ./bin/BOOT_TH05V13_v13.hex
python3 rdwr_phy62x2.py -p COM11 -r we 0x10000 ./bin/TH05V13_v13.bin
``` 

## Событие Open/Close и счет импульсов

С версии 1.2 поддерживается опрос вывода подключенного к геркону или контакту, замыкающемуся на GND.

Максимальная частота переключения - 100 раз в секунду.

Если контакт имеет дребезг, тогда желательно зашунтировать контакт конденсатором.

При замыкании или размыкании передается блок из 5 BLE реклам следующих друг за другом через период в 50 мс.

При каждом событии "Open" прибавляется счетчик. 

Значение счетчика передается совместно с каждым событием "Open/Close".

Входной контакт на плате термометра:
* На [THB1](https://pvvx.github.io/THB1) - маркирован как `RX`
* На [THB2](https://pvvx.github.io/THB2) - маркирован как `RX`
* На [BTH01](https://pvvx.github.io/BTH01/) - маркирован как `RX2`
* На [TH05_V1.3](https://pvvx.github.io/TH05-v1.3)  - маркирован как `RX0`
* На [TH05_V1.4](https://pvvx.github.io/TH-05) - маркирован как `RX2`
 
![image](https://github.com/pvvx/THB2/assets/12629515/09f6f810-f2e2-4b61-9c84-f7c3770bb76a)

## Вывод управления внешним устройством по температуре и/или влажности

Контакт на печатной плате с маркировкой "TX" или "TX2" управляется с помощью уставок с гистерезисами по температуре и влажности.
Имеется возможность переключения на инверсное управление выводом.

Настройка производится в PHY62x2BTHome.html.

Работа выхода назначается с помощью установки значения гистерезиса:
* Если значение гистерезиса равно нулю - переключений не будет.
* Если значение гистерезиса больше нуля - переключение (включение) произойдет при значении ниже уставка + гистерезис.
* Если значение гистерезиса меньше нуля - переключение (включение) произойдет при значении выше уставка + гистерезис.

---

## Сборка прошивки.

Для сборки прошивки используется GNU Arm Embedded Toolchain.

Для работы в Eclipce используете импорт проекта и установите toolchain.path.

Дополнительная информация по чипам [PHY62xx](https://github.com/pvvx/PHY62x2).
