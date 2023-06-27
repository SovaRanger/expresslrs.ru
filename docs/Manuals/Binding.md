---
description: Биндим ELRS легко и просто
---
??? info "Видео версия от Joshua Bardwell"
    <figure markdown>
    <iframe width="560" height="315" src="https://www.youtube.com/embed/MFFUsN9ZHSU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </figure> 

# Сверяем версию прошивок:

``` mermaid
graph LR
  A[Проверяем версию прошивки] --> B{Прошивка 3.х};
  B -->|Нет| C[Прошиваем 3.х];
  C --> B;
  B ---->|Да| E[Вводим фразу на WiFi странице];
```

## Проверяем версию прошивки передатчика:

=== "Через Lua Скрипт"

    Потребуется [Lua скрипт ELRS](https://github.com/ExpressLRS/ExpressLRS/blob/3.x.x-maintenance/src/lua/elrsV3.lua?raw=true) (правой кнопкой, сохранить как *.lua). Скачайте и закиньте на флешку аппы, в папку `/Scripts/Tools`.
    Чтобы открыть скрипт на аппаратуре зажмите кпопку ++"SYS"++ и выберите `ExpressLRS`.

    <figure markdown>
    ![Lua Script](/../assets/images/lua1.jpg)
    </figure>

    Если скрипт не открывается и висит на `Loading...`, проверь что в модели выставлен Internal CRSF для внутреннего передатчика, либо External CRSF для внешнего. [Настройка аппаратуры](/Manuals/Firmware/Transmitters/tx-prep)

    <figure markdown>
    ![InternalRF BW](/../assets/images/txprep-bw-internalRF.jpg)
    </figure>

    Листаем скрипт в самый низ и смотрим версию.

=== "На экране внешнего модуля"
    Если у вашего внешнего передатчика есть экран, то версия прошивки показывается прямо там
    <figure markdown>
    ![Oled](/../assets/images/OLED-version_info.jpg)
    </figure>

## Если ваш передатчик имеет версию 3.x.x 

Переходим в Lua Script ELRS, выбираем пункт `Wifi Connectivity` в скрипте, а потом нажмите `Enable Wifi`. Нажмите ОК еще раз, чтобы включить WiFI на передатчике. Подключитесь к сети `ExpressLRS TX` с паролем `expresslrs`.

<figure markdown>
![Lua3](/../assets/images/lua/wifi-bw.png)
</figure>

<figure markdown>
![WiFi Hotspot](/../assets/images/WifiHotspotTX.png)
</figure>

!!! danger "Регион прошивки"
    Обратите внимание на регион прошивки, он должен совпадать и на приемнике и на передатчике и быть ISM2G4, в редком случае вам может приехать из магазина EU/LBT версия, имеющая ограничения, тогда придется перепрошить.

В поле ``Binding Phrase`` вводим уникальное слово и нажимаем сохранить. По этому слову приемник будет находить передатчик. Никаких дополнительных процедур для бинда не требуется, все автоматически.
Пожалуйста не вбивайте 123456 и тд, судя по ELRS чату таких людей очень много, и когда-нибудь такие ленивые люди пересекуться на полетушках и будут биндится друг к другу.

<figure markdown>
![Wifi TX](/../assets/images/bind_tx.jpg){ width="300" }
</figure>


## Если ваш передатчик имеет версию 2.x.x 

Прошиваем на ``3.x.x`` прошивку по инструкциям:

[Инструция прошивки внутреннего передатчика](/Manuals/Firmware/Transmitters/Flashing-internal-tx)

[Инструция прошивки внешнего передатчика](/Manuals/Firmware/Transmitters/Flashing-external-tx)


## Проверяем версию прошивки приемника:

Если у вас встроенный в полетник SPI приемник то вам в [эту инструцию](/Manuals/Firmware/Recievers/spi-reciever)

Подайте питание на полетник. Это можно сделать как по USB, так и воткнув батарею в дрон. Диод на приемнике начнет медленно мигать. Через 20-30 секунд диод на приемнике начнет моргать быстро, значит он начал раздавать WiFi.

<figure markdown>
![LEDSEQ_WIFI_UPDATE](https://cdn.discordapp.com/attachments/738450139693449258/921065813983760384/LEDSEQ_WIFI_UPDATE_2_3.gif)
</figure>

Подключитесь к сети `ExpressLRS RX` с паролем `expresslrs`.

<figure markdown>
![WiFi Hotspot](/../assets/images/WifiHotspot.png)
</figure>

Откройте браузер и перейдите на http://10.0.0.1/
Версия прошивки указана в шапке сайта

## Если вы видите версию 3.x.x

!!! danger "Регион прошивки"
    Обратите внимание на регион прошивки, он должен совпадать и на приемнике и на передатчике и быть ISM2G4, в редком случае вам может приехать из магазина EU/LBT версия, имеющая ограничения, тогда придется перепрошить.

В поле ``Binding Phrase`` вводим уникальное слово и нажимаем сохранить. По этому слову приемник будет находить передатчик. Никаких дополнительных процедур для бинда не требуется, все автоматически.
Пожалуйста не вбивайте 123456 и тд, судя по ELRS чату таких людей очень много, и когда-нибудь такие ленивые люди пересекуться на полетушках и будут биндится друг к другу.

<figure markdown>
![Wifi TX](/../assets/images/bind_tx.jpg){ width="300" }
</figure>

## Если вы видите версию 2.х.х

Прошейте приемник до 3.х.х [по инструкции](/Manuals/Firmware/Recievers/external-reciever)

