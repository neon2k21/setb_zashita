# Таблица ACL для пользователей
|Категория пользователя|	Источник (IP-адрес или диапазон)|	Назначение (ресурс/сеть)|	Протокол|	Порты	|Действие|	Примечания|
|-|-|-|-|-|-|-|
|Бухгалтерия	|178.0.10.0/24|	Сервер БД	|TCP	|1433, 3306|	Разрешить|	Доступ к базе данных для бухгалтерского ПО|
|Бухгалтерия	|178.0.10.0/24|	Сервер приложений	|TCP|	8080, 443|	Разрешить|	Доступ для работы с внутренними системами|
|Отдел кадров	|178.0.20.0/24|	Сервер БД	|TCP|1433, 3306|	Разрешить|	Доступ к базе данных для управления персоналом|
|Отдел кадров	|178.0.20.0/24|	Сервер приложений|	TCP|	8080, 443|	Разрешить|	Доступ к HR-системам|
|Административный отдел|	178.0.30.0/24|	Сервер электронной почты	|TCP	|25, 587, 993	|Разрешить	|Корпоративная почта|
|Административный отдел	|178.0.30.0/24|	Сервер приложений	|TCP	|8080, 443	|Разрешить|	Взаимодействие с административными сервисами|
|Хозяйственный отдел	|178.0.40.0/24|	Внутренняя сеть|	Все|	Все|	Запретить	|Ограничение доступа к критичным ресурсам|
|Хозяйственный отдел	|178.0.40.0/24|	Сервер приложений	|TCP|	8080|	Разрешить	|Только базовые сервисы|
|Проектный отдел|	178.0.50.0/24	|Сервер приложений	|TCP|	22, 8080	|Разрешить	|SSH и доступ к веб-приложениям|
|Проектный отдел	|178.0.50.0/24	|Сервер БД|	TCP|	1433, 3306	|Разрешить|	Доступ к базе данных для анализа проектов|
|IT-отдел (УИТ и АСУ)|	178.0.60.0/24|Все ресурсы	|Все|	Все	|Разрешить|	Полный доступ для администрирования|
|IT-отдел (УИТ и АСУ)|	178.0.60.0/24|Веб-сервер (DMZ)	|TCP	|80, 443	|Разрешить	|Управление веб-сайтами и внешними системами|
|Гостевые пользователи|	178.0.70.0/24|Интернет	|TCP/UDP	|Все	|Разрешить	|Только внешний доступ|
|Гостевые пользователи|	178.0.70.0/24|Внутренняя сеть|	Все	|Все	|Запретить|	Отсутствие доступа к внутренним ресурсам|
|Удалённые пользователи (RDP)|	178.0.80.0/24|	Сервер RDP	|TCP|	3389	|Разрешить|	RDP-доступ для удалённого управления|
|Удалённые пользователи (RDP)|	178.0.80.0/24|	Сервер приложений	|TCP|	8080, 443|	Разрешить|	Доступ к веб-приложениям|
|Системные администраторы|	178.0.60.100 - 178.0.60.200|	Серверная сеть|	Все|	Все|	Разрешить|	Полный доступ для обслуживания серверов|
|Системные администраторы	|178.0.60.100 - 178.0.60.200|	Почтовый сервер (DMZ)|	TCP|	25, 587, 993|	Разрешить	|Управление почтовыми сервисами|
|Внешние пользователи (VPN)|	178.0.100.0/24	|Внутренняя сеть|	Все	|Все|	Разрешить	|Доступ через защищённые каналы VPN|
|Внешние пользователи (VPN)|	178.0.100.0/24|	Веб-сервер (DMZ)|	TCP|	80, 443|	Разрешить|	Работа с корпоративными ресурсами через VPN|
|Пользователи почтового сервера|	Все	|Почтовый сервер (DMZ)	|TCP|	25, 110, 143|	Разрешить|	Получение и отправка писем|
|Веб-пользователи|	Все|	Веб-сервер (DMZ)|	TCP|	80, 443|	Разрешить|	Доступ к веб-ресурсам компании|
|Мониторинг и SOC|	178.0.90.0/24	|Все внутренние ресурсы|	TCP/UDP|	Все	|Разрешить|	Доступ для мониторинга и анализа безопасности|


#   Матрица доступа для центрального офиса
|Категория пользователя	|Сервер БД|	Сервер приложений|	Почтовый сервер (DMZ)|	Веб-сервер (DMZ)|	Сервер RDP	|Серверная сеть|	Интернет|	Внутренняя сеть (другие VLAN)|
|-|-|-|-|-|-|-|-|-|
|Бухгалтерия	|✅	|✅	|❌	|❌	|❌	|❌	|❌	|❌|
|Отдел кадров	|✅	|✅	|❌	|❌	|❌	|❌	|❌	|❌|
|Административный отдел	|❌	|✅	|✅	|❌	|❌	|❌	|✅	|❌|
|Хозяйственный отдел	|❌	|✅ (ограниченно)	|❌	|❌	|❌	|❌	|❌	|❌|
|Проектный отдел	|✅	|✅	|❌	|❌	|❌	|❌	|✅	|❌|
|IT-отдел (УИТ и АСУ)	|✅|	✅	|✅	|✅	|✅	|✅	|✅	|✅|
|Гостевые пользователи	|❌	|❌	|❌	|❌	|❌	|❌	|✅	|❌|
|Удалённые пользователи (RDP)	|❌|	✅	|❌	|❌	|✅	|❌	|❌	|✅|
|Системные администраторы	|✅	|✅	|✅	|✅	|✅	|✅	|✅	|✅|
|Внешние пользователи (VPN)	|✅	|✅	|✅	|✅	|❌	|❌	|✅	|✅|
|Пользователи почтового сервера	|❌	|❌	|✅	|❌	|❌	|❌	|✅	|❌|
|Веб-пользователи	|❌	|❌	|❌	|✅	|❌	|❌	|✅	|❌|
|Мониторинг и SOC	|✅	|✅	|✅	|✅	|✅	|✅	|✅	|✅|


#   Таблица правил фильтрации для межсетевого экрана
|№	|Источник	|Назначением	|Порт/Протокол|	Действие	|Примечание|
|-|-|-|-|-|-|
|1	|VLAN 10 (Бухгалтерия)|	Сервер БД	|3306/TCP (MySQL)	|Разрешить	|Доступ бухгалтерии к базе данных для финансовых операций
|2	|VLAN 20 (Отдел кадров)|	Сервер приложений|	8080/TCP|	Разрешить|	Доступ отдела кадров к приложению для управления сотрудниками
|3	|VLAN 30 (Администрация)|	Почтовый сервер (DMZ)	|25, 587/TCP (SMTP)|	Разрешить|	Администрация отправляет почту
|4	|VLAN 50 (Проектный отдел)|	Сервер приложений|	8080/TCP	|Разрешить|	Доступ для работы с проектами
|5	|VLAN 60 (IT-отдел)|	Все внутренние сети	|Все	|Разрешить|	IT-отдел имеет полный доступ к сетевым ресурсам
|6	|VLAN 70 (Гостевой Wi-Fi)|	Интернет	|80, 443/TCP (HTTP/HTTPS)	|Разрешить|	Гостевые пользователи имеют доступ только к внешним ресурсам
|7	|Удалённые пользователи (VPN)|	Сервер RDP	|3389/TCP	|Разрешить	|RDP доступ для удалённых сотрудников
|8	|VLAN 100 (VPN)|	Сервер БД, Сервер приложений|	3306/TCP, 8080/TCP	|Разрешить|	Доступ через VPN к корпоративным ресурсам
|9	|Почтовый сервер (DMZ)|	Интернет	|25, 587, 993/TCP	|Разрешить|	Обеспечение почтовой связи через DMZ
|10	|Веб-сервер (DMZ)|	Интернет	|80, 443/TCP	|Разрешить|	Доступ к веб-сайту организации
|11	|VLAN 90 (Серверная сеть)|	SOC	|Все	|Разрешить	|Доступ для мониторинга и анализа
|12	|Гостевой Wi-Fi|	Внутренние сети|	Все|	Запретить|	Ограничение доступа гостей к внутренним ресурсам
|13	|Внешние IP-адреса	|Почтовый сервер (DMZ)|	25, 587, 993/TCP|	Разрешить	|Приём почты из внешних источников
|14	|Внешние IP-адреса|	Веб-сервер (DMZ)	|80, 443/TCP|	Разрешить|	Публичный доступ к веб-серверу
|15|	Все|	Все|	Все|	Запретить|	Базовое правило блокировки: запрещено всё, что не разрешено явно

- [Назад](../Main.md)
