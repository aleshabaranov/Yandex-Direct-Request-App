# Yandex-Direct-Request-App
Данный скрипт позволяет запрашивать отчеты Yandex Директа с дальнейшим формированием файлов csv. Используется язык Python. Также имеется скомпилированная версия скрипта, которая позволяет использовать скрипт без понимания кода и наличия установленного языка Python на ПК. При необходимости в программе можете запросить у меня в телеграме https://t.me/aleshabaranov , в дальнейшем поделитесь опытом использования.

Данная программа помогает при выгрузке большого объема данных из Яндекс Директа, а также формирует полученные данные в файл .csv.

Для корректной работы программы требуется:
-API токен рекламного агентства в Директе. Подробно о получении токена по ссылке https://yandex.ru/dev/direct/doc/dg/concepts/access.html

В работе скрипта используется Python с установленными библиотеками requests, pandas

Программа представлена в 2х вариантах - скрипт python и скомпилированный .exe файл, который позволяет запустить и использовать программу на любом устройстве с ОС Windows без установленного python и необходимых библиотек.

Следуя четким указаниям программы вы получите сформированный отчет с необходимыми вам группировками и метриками.

Вам необходимо указать токен вашего агентства и логин клиента(без @yandex.ru), указанный в Директе. Подробная информация о получении токена представлена в официальной документации Яндекса по ссылке https://yandex.ru/dev/direct/doc/dg/concepts/register.html 
![image](https://user-images.githubusercontent.com/61497343/191431482-a20de544-fd0e-4f51-9d2a-d0250e877036.png)


После этого вы увидите список доступных группировок и метрик, из которых вы сможете сформировать необходимый вам отчет. Важно, чтобы все показатели вводились также как указано в словаре, с соблюдением всех регистров, в противном случае программа не сможет выполнить корректный запрос к Директу и закончится ошибкой. Более подробно о допустимых полях можно посмотреть тут https://yandex.ru/dev/direct/doc/reports/fields-list.html . Программа использует CUSTOM_REPORT, т.к. данный тип отчета позволяет получать максимальное количество полей.
![image](https://user-images.githubusercontent.com/61497343/191431612-963a6bc1-1c86-4436-b431-fe908ff7c356.png)



В случае, если в полях для отчета вы выбрали Conversions, далее потребуется выбрать ID необходимых конверсий из Я.Метрики, период дат для отчета, а также модель атрибуции, по которой вас интересуют данные. Если вы не ввели Conversions, то этапы с запросом конверсий и атрибуции пропускаются.
![image](https://user-images.githubusercontent.com/61497343/191431664-6a6d1867-4db5-4b13-932e-722c4570a1c2.png)



После этого необходимо указать название отчета, которое потребуется в случае формирования файла .csv. Программа начнет выполнять запрос к Директу, если в отчете указан большой объем данных, то запросы будут повторяться каждые 10 секунд до момента готовности отчета.
![image](https://user-images.githubusercontent.com/61497343/191431703-9fe7b184-55c7-4e2b-9875-712db1665313.png)


В случае успешного создания и выгрузки отчета вы увидите сообщение, о том, что работа выполнена и вам останется только нажать Enter для формирования .csv 

Отчет для формата .csv ограничен 10000000 строк, формирование отчета с таким объемом данных может занять 30 минут и файл будет иметь вес более 300 мб.


Действия касательно получения токена можно изучить по ссылке https://yandex.ru/dev/direct/doc/dg/best-practice/quick-start.html

1.Создайте аккаунт в Директе, который будете использовать как разработчик приложений (если вы работаете в агентстве, то нужно получить токен для агентского аккаунта)
2.На странице Настройки API https://direct.yandex.ru/registered/main.pl?cmd=apiSettings  нажмите ссылку Получить доступ к API и примите пользовательское соглашение.
3.Зарегистрируйте приложение по ссылке на сервисе Яндекс.OAuth https://yandex.ru/dev/direct/doc/dg/concepts/register.html#oauth . После регистрации приложения вы получите уникальное значение Client ID, которое нужно подставить в урл https://oauth.yandex.ru/authorize?response_type=token&client_id=’ваш ClientID’ и вы перейдете на страницу с токеном.
4. После прохождения всех шагов вы получите уникальный токен для вашего агентства, который нужно сохранить в надежном месте. В дальнейшем он понадобится для совершения запросов к серверам Директа. С помощью данного токена и логина вашего клиента вы сможете получать данные по всем клиентам, которые закреплены за вашим агентским кабинетом.

В случае работы со скриптом необходимо установить на компьютер python и все библиотеки указанные в скрипте. Установить стандартный интерпретатор Python, запустить код и следовать указанным шагам. Логика работы скрипта аналогична скомпилированной программе, однако для его работы требуется установленный язык Python, IDE - среда разработки, установленные библиотеки. Скомпилированная программа может запускаться без наличия установленного Python на ПК. Программа не требует установки, запускается через exe файл и формирует отчет с csv в папку, где она находится.

В случае, если при вводе информации были введены неверные данные (например, некорректный логин, токен, неправильно написанные необходимые поля, несоблюдение регистра, некорректно указан формат даты) программа закроется выдав ошибку, для повторения запроса ее необходимо запустить снова. Возможно, в дальнейшем логика программы пойдет в сторону указания пользователю на его ошибки при вводе данных, однако в данный момент нужно привыкнуть к использованию программы, что происходит после совершения нескольких запросов.

Получить ответы на ваши вопросы при взаимодействии с программой вы можете в телеграмме у меня https://t.me/aleshabaranov . Также поделиться опытом вашего использования программы.
