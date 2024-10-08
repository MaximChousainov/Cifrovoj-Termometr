# Описание
Проект «Цифровой термометр» — это инструкция по созданию устройства, считывающего температуру с датчика и отправлящего полученную температуру на сервер HTTP. Проект состоит из двух частей, устройство, или прибор, и сервис HTTP. Устройство «разговаривает» с сервисом посредством запросов HTTP, передавая на сервис текущую температуру. Сервис собирает и сохраняет данные: время и температуру.

## Использование
Прибор можно использовать в лабораторных физических опытах, таких как кристаллизация и плавление жидкостей, в частности воды. У прибора выносной термометр, позволяющий поместить его в жидкость, заморозить вместе с жидкостью и, подключив термометр к прибору, провести опыт плавления. Так как прибор может питаться от аккумулятора, его можно поместить в морозильную камеру и провести опыт кристаллизации. Данные, собранные прибором, можно использовать для построения графиков изменения температуры во времени.

## Компоненты
Прибор содержит экран, кнопку, датчик температуры и основывается на микроконтроллере ESP8266-12E. Датчик температуры подключается к прибору через провод. Прибор состоит из следующих компонентов:
- датчика температуры DS18B20;
- микроконтроллера ESP8266-12E;
- экрана OLED ($128\times64$ px);
- стабилизатора напряжения с $5$ В до $3{,}3$ В или блока питания с аккумулятором;
- резисторов и нажимной кнопки.


## Работа
При включении цифрового термометра, прибор каждую секунду считывает температуру с датчика температуры и отображает её на экране. Также прибор подключается к беспроводной сети. При нажатии на кнопку, начинается опыт: прибор отправляет запрос на сервис о начале опыта и в дальнейшем отправляет ежесекундно запросы с текущей температурой. Повторное нажатие на кнопку останавливает опыт, т. е. прибор перестаёт посылать запросы на сервис с текущей температурой.

Сервис, при запросе о начале опыта, создает новый архив. При запросе с температурой, сервис сохраняет её вместе со временем получения запроса в созданный архив.


## Характеристики
Предлогаемый датчик температуры работает в диапазоне от $-55$&deg; C до $125$&deg; C. Среднее потребление прибора $0{,}07$ А или $0{,}23$ Вт.

# Организация папок проекта
Инструкция по созданию цифрового термометра содержится в папке «Документация» в архиве «Цифровой_термометр.pdf». 
В архиве дается детальный разбор составных частей прибора и схема их соединений, предоставляется
вариант автономии устройства в плане энергии, описывается алгоритм работы прибора и прилагается блок-схема этого алгоритма, описывается алгоритм работы сервера, даются инструкции по установке программной части прибора и сервиса. Остальные архивы в папке это архивы XeLaTeX, из которых производится PDF.

В папке «Прошивка» находится код прошивки микроконтроллера ESP8266-12E под платформу Espruino.

В папке «Сервер» находится код сервера на python.