# Rakcheat anticheat

Данный античит разработан на основе [Nex-AC](https://github.com/NexiusTailer/Nex-AC) и интегрирует в него проверки из [rakcheat](https://github.com/f0Re3t/rakcheat).  
Все проверки и защиты из rakcheat были оптимизированы, а так же добавлены иные методы.  

Ниже описаны основные различия с оригинальным Nex-AC.

## Внешние функции

В OnCheatDetected был добавлен дополнительный параметр "code2", теперь он объявляется так:

```pawn
forward OnCheatDetected(playerid, ip_address[], type, code, code2);
```

Этот параметр идентичен таковому в OnCheatWarning и предназначен для понимания того, какая из проверок сработала внутри кода античита.

## Настройки по умолчанию

Отключена поддержка большинства механик одиночной игры, вывод статистики срабатываний при выключении сервера и чтение/запись внешнего конфиг файла. Также по умолчанию отключена поддержка NPC-ботов, но если вы используете их на своем сервере, то можете включить это (таким же образом, как и в стандартном античите):

```pawn
#define AC_USE_NPC true
#include <rakcheat>
```

Среди прочего:
* Максимальное количество входящих игроков с одного IP адреса было повышено с 1 до 3.
* Максимальное количество неудачных попыток входа в RCON было повышено с 1 до 3.

## Коды античитов

Добавлен новый код 53 (Anti-Fast movement), остальные изменения и доработки были добавлены в существующие коды античитов. Все они имеют свой подкод (code2), по которому можно понять, что срабатала именно новая проверка из rakcheat, даже если она будет с тем же основным кодом, что был в базовом античите.

Если вы настраиваете античит из конфиг файла "nex-ac_settings.cfg", то рекомендуется удалить его из папки "scriptfiles" и сгенерировать новый, если предыдущий был сгенерирован оригинальным Nex-AC (в связи с изменением количества кодов античита).

Кому нужна более подробная техническая информация по поводу всех добавленных проверок и того, что они добавляют и как они работают - берите diff checker и сравнивайте с базовым античитом. Возможно, кому-то это будет полезно.
