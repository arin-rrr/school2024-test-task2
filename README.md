# Тестовое задание для отбора на Летнюю ИТ-школу КРОК по разработке

## Условие задания
Один развивающийся и перспективный маркетплейс активно растет в настоящее время. Текущая команда разработки вовсю занята тем, что развивает ядро системы. Помимо этого, перед CTO маркетплейса стоит задача — разработать подсистему аналитики, которая на основе накопленных данных формировала бы разнообразные отчеты и статистику.

Вы — компания подрядчик, с которой маркетплейс заключил рамочный договор на выполнение работ по разработке этой подсистемы. В рамках первого этапа вы условились провести работы по прототипированию и определению целевого технологического стека и общих подходов к разработке.

На одном из совещаний с Заказчиком вы определили задачу, на которой будете выполнять работы по прототипированию. В качестве такой задачи была выбрана разработка отчета о наиболее популярных категориях товаров, продаваемых во время подготовки новогодних подарков покупателями.

Аналитики со стороны маркетплейса предоставили небольшой срез массива данных (файл format.json) о совершенных покупках пользователей за 4-й квартал 2023 года, на примере которого вы смогли бы ознакомиться с форматом входных данных. Каждая запись данного среза содержит следующую информацию:
- Дата и время оформления заказа;
- Корзина.

В пояснительной записке к массиву данных была уточняющая информация относительно формате данных, представленных в корзине. Так, например, корзина - это массив однотипных сведений о купленных товаров, определяемых следующим набором данных:
- Идентификатор товара;
- Наименование товара;
- Категория.

В свою очередь сведения о категории представлены в следующем виде:
- Идентификатор категории;
- Наименование категории.

Необходимо разработать отчет, определяющий категории товаров, наиболее популярные перед Новым годом. Если популярных категорий товаров больше, чем одна, отчет должен показывать их все. Предновогодним периодом будем считать срок с 1 по 31 декабря.

Требования к реализации:
1. Реализация должна содержать, как минимум, одну процедуру (функцию/метод), отвечающую за формирование отчета, и должна быть описана в readme.md в соответствии с чек-листом;
2. В качестве входных данных программа использует json-файл (input.json), соответствующий структуре, описанной в условиях задания;
3. Процедура (функция/метод) формирования отчета должна возвращать строку в формате json следующего формата:
   - {«categories»: [«Бытовая техника»]}
   - {«categories»: [«Бытовая техника», «Косметика»]}
4. Найденная в соответствии с условием задачи категория должна выводиться в изначальном наименовании, приведенном в файле с входными данными. Если таких категорий несколько, то на вывод они все подаются в алфавитном порядке.

## Автор решения 
Смахтина Арина Вадимовна

## Описание реализации
1) Импортированы библиотеки json для работы с json-файлами и datetime для работы с датами
2) Внутри программы реализована функция get_json, которая принимает название json-файла, в котором дан срез массива данных о совершенных покупках пользователей за 4-й квартал 2023 года
3) После данные из файла чистаются и сохраняются в template, создан словарь для подсчитывания вхождений каждой категории (которая удовлетворяет условиям по дате покупки)
4) Проходимся по массиву template, если дата подходящая, т.е. от 1 декабря до 31 декабря, то добавляем категорию в category. При этом считается максимальное количество вхождений
5) Создан массив res_list, в котором сохраняем категории, которые покупали наибольшее кол-во раз. Сортируем этот массив
6) Создаём словарь to_json, который и возвратит функция.
7) В конце вызывается функция и принтуется её результат
## Инструкция по сборке и запуску решения
Так как в условии сказано, что входные данные - в файле input.json, то программу можно запустить либо в любой IDE, но файл должен быть в той же папке, что и программа
Либо через командную строку cmd: переходим в папку, где хранятся программа и input.json через cd .../KPOK. После запускаем программу через python main.py
