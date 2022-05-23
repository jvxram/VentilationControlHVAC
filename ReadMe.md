# VentilationControlHVAC

----
#### Назначение
Графическая формочка управления щитом общеобменной приточно-вытяжной установки **HVAC** (далее по тексту щитом) применяется для телеметрии и дистанционного управления (супервизорный режим внешних контуров каскадных схем управления) аппаратурой **SIEMENS**, **Schneider Electric** с 1999-го года:
 - дает команду на автопрогон настроек регулятора внутреннего контура,
 - считывает настройки регуляторов,
 - выдает настройки на регуляторы,
 - выдает задание на регулирование,
 - включает и отключает работу щита.

Регуляторы программные на контроллере щита.
Для управления каждым щитом открывается своя формочка, на которой вводятся параметры работы

----
#### Объемы доработок (вступительная часть):
 - Сделать на формочке выбор адреса щита в сети **ModBUS-TCP** (используемых адресов не должно быть в списке доступных адресов),
 - Формочка ведущая (опрашивает), все щиты - ведомые (отвечают на запросы),
 - Возможно понадобится написать отдельную серверную компоненту по опросу щитов по их адресам и раздаче опрошенных данных на формочки по их запросам, индикатор которой вывести например в индикаторы на панели задач,
 - Вставить скрипты-обработчики нажатия кнопок,
 - Написать обработчики,
 - Внизу подписать названия каналов и названия режимов,
 - Сделать из режимов группу, чтобы выбирался только один из них,
 - Делать неактивными виджеты (адрес, прочитать/записать настройки), которые не могут отдавать команду на установку, когда она в работе,
 - Читать и писать настройки из внешнего **SQL Server**-а по адресу установки,
 - Сделать автопрогон настроек регулятора, считать их с контроллера в формочку как оптимальных и записать их в базу на внешнем SQL Server-е,
 - Использовать настройки регуляторов контуров, полученные по результатам расчета замкнутой системы регулирования (см. отдельный проект),
 - Переписать расчет переходного процесса замкнутой системы регулирования (см. в отдельный проект) как отдельного клиента с C++ на Python

![IMG_20160928_152215](https://user-images.githubusercontent.com/104857185/169311708-07b7b03a-a0fc-4fd0-a122-0f73b721b21e.jpg)
![IMG_4704](https://user-images.githubusercontent.com/104857185/169308673-81a780ba-8a2d-46db-ab37-a9f41d53fa34.JPG)
![IMG_4486](https://user-images.githubusercontent.com/104857185/169309000-4f485313-a44b-4f15-818e-b0a76adfc1ff.JPG)
![IMG_2730](https://user-images.githubusercontent.com/104857185/169309761-4aae6a09-035f-40b2-98dc-40d79ec5ff9f.JPG)
![IMG_4547](https://user-images.githubusercontent.com/104857185/169310149-21e65ddf-7baa-45be-a14c-aa3a2d774197.JPG)
![IMG_4778](https://user-images.githubusercontent.com/104857185/169310532-a605a20f-8389-42ef-9c34-928f5b01c33a.JPG)
![IMG_4793](https://user-images.githubusercontent.com/104857185/169310808-5151ae47-95cf-4c17-8756-ea7f3cd65ec5.JPG)

#### Ссылочная литература
Каталоги 1998-го (остался только в печатном виде), 2002-го и 2005-го годов на сервере в папках:
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS`
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\Synco HVAC`
 - `P:\Техническая информация\Электротехника и КИПиА\Schneider Electric` 

Техническая документация по SCADA-системам фирмы-изготорителя на сервере в папках:
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\Desigo Insight`
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\Desigo CC`
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\Cerberus Pro`
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\DMS8000`
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\SCADA Win CC`
 - `P:\Техническая информация\Электротехника и КИПиА\SIEMENS\SiPass`

#### Примечания:
 - Нужны новые **DDK** и **SDK** фирмы-изготовителя контроллеров HVAC (имеющиеся в наличии работают со старыми моделями аппаратуры)
 - В случае использования SCADA-системы фирмы-изготовителя аппаратуры **OPC-сервер** ставится дополнительно поверх нее. Для полноценного функционирования SCADA-систему ставить на **Windows Server** с 4-м **.Net FrameWork**-ом, с **IIS**, с **SQL Express** (после установки зайти в настройки и переподключиться на внешний **SQL Server**). Функционал **OPC-сервер**-а разрешается в USB-вом ключе по дополнительному договору за ежегодную дополнительную оплату фирме-изготовителю

----
Наработки по аналогам SCADA-системы **Desigo Insight** фирмы SIEMENS в том числе есть у **ООО ИПК Индустрия** (г. Мытищи)
см. https://www.facebook.com/ipkindustriya/ 
