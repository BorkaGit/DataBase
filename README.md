
English:

 #### Programming assignment: The final task of the course ####
You need to write a C++ program that implements a simple database (abbreviated as "DB"). The program will communicate with the user through standard input and output (streams stdin and stdout).

We will store in our database pairs of the following form: date, event. Define date as a string the form Year-Month-Day, where Year is number from 0 to 9999 inclusive, Month - number of month from 1 to 12 inclusive, Day - number of day from 1 to 31 inclusive.

Year, Month and Day are always separated by exactly one hyphen (-) and no other character. Define event as a string of arbitrary text characters without separators (spaces, tabs, etc.). An event cannot be an empty string. Many different events may occur on the same date - the database must be able to save them all. Identical events occurring on the same day do not need to be saved - only one of them needs to be saved.

Our database must understand certain commands to be able to interact with it:

```objectivec
- adding an event:                           Add Date Event
- deleteting an event:                       Del Date Event
- deleting multiple evenets:                 Del Date
- search for events:                         Find Date
- print all events:                          Print
```
All commands, dates and events are separated by spaces when entered. The commands are read from the standard input. There can be exactly one command per line, but multiple commands can be entered on multiple lines. Blank lines may also be entered - these must be ignored and new commands will continue to be processed on subsequent lines.

Adding an event
When adding an event, the database must memorize it and then display it when searching (using the Find command) or printing (using the Print command). If it is entered correctly, the program must not display anything.

Deleting events
You can delete only previously added events. If the event is found and removed, the program should output the "Deleted successfully" string (without inverted commas). If the event is not found on the specified date the "Event not found" string (without inverted commas) should be output.

Deleting multiple events
This command removes all previously added events on a specified date. The program should always output the line "Deleted N events" where N is the number of all found and deleted events. N may be equal to zero if there were no events on the specified date.

Search for events
Look for and print the previously added events on the specified date. The program should print only the events themselves, one per line. The events have to be sorted in ascending order of the lines compared to each other (string type).

Print all events
This command can be used to display the full content of our database. The program must print all Date Event pairs, one per line. All pairs must be sorted by date and events within one date must be sorted in ascending order of comparison of lines to each other (string type). Dates must be formatted in a special way: YYYY-MM-DD, where Y, M, D are the digits of the year, month and day respectively. If any number has fewer digits, it should be padded with zeros, for example, 0001-01-01 is the first of January of the first year.

Handling input errors
If a user has entered an unknown command, the program must report this by outputting the "Unknown command: COMMAND" string, where COMMAND is the command entered by the user. The command is the first word in the string (before a space).

If the user entered a date in the wrong format where it was expected, the program should print "Wrong date format: DATE", where DATE is what the user entered instead of the date (before the space).

If the date format is correct, but the date itself is incorrect, it should print a more specific problem:

"Month value is invalid: MONTH", where MONTH is an invalid month number, e.g. 13 or 0.
"Day value is invalid: DAY", where DAY is an invalid day number in the month, for example 39 or 0.
The year value does not need to be checked separately.
It is not necessary to check the calendar correctness of dates: the number of days in each month is 31, leap years do not need to be taken into account.
If both month and day are incorrect, one error message per month must be printed.
After any error message is entered and printed the program should terminate.

##### Examples #####
Correct input:

```objectivec
Add 0-1-2 event1
Add 1-2-3 event2
Find 0-1-2
Del 0-1-2
Print
```
Output:

```objectivec
event1
Deleted 1 events
0001-02-03 event2
```
Incorrect date format:
```objectivec
Add 0-13-32 event1
```


Output:
```objectivec
Month value is invalid: 13
```

#### Задание по программированию: Финальная задача курса ####

Необходимо написать программу на С++, которая реализует работу с простой базой данных (сокращённо «БД»). Программа будет общаться с пользователем через стандартный ввод и вывод (потоки *stdin* и *stdout*).

Будем хранить в нашей БД пары вида: дата, событие. Определим дату как строку вида *Год-Месяц-День*, где *Год* — это число от 0 до 9999 включительно, *Месяц* — это номер месяца от 1 до 12 включительно, *День* — это номер дня от 1 до 31 включительно.

*Год*, *Месяц* и *День* всегда разделяются ровно одним символом дефиса (-) и никаким другим. Событие определим как строку из произвольных печатных символов без разделителей внутри (пробелов, табуляций и пр.). Событие не может быть пустой строкой. В одну и ту же дату может произойти много разных событий — БД должна суметь их все сохранить. Одинаковые события, произошедшие в один и тот же день сохранять не нужно — достаточно сохранить только одно из них.

Наша БД должна понимать определённые команды, чтобы с ней можно было взаимодействовать:
```objectivec
- добавление события:                        Add Дата Событие
- удаление события:                          Del Дата Событие
- удаление всех событий за конкретную дату:  Del Дата
- поиск событий за конкретную дату:          Find Дата
- печать всех событий за все даты:           Print
```
Все команды, даты и события при вводе разделены пробелами. Команды считываются из стандартного ввода. В одной строке может быть ровно одна команда, но можно ввести несколько команд в несколько строк. На вход также могут поступать пустые строки - их следует игнорировать и продолжать обработку новых команд в последующих строках.

##### Добавление события #####
При добавлении события БД должна его запомнить и затем показывать его при поиске (командой Find) или печати (командой *Print*). В случае корректного ввода программа ничего не должна выводить на экран.

##### Удаление события #####
Удалить можно только ранее добавленные события. Если событие найдено и удалено, то программа должна вывести строку *«Deleted successfully»* (без кавычек). Если событие в указанную дату не найдено, то программа должна вывести строку *«Event not found»* (без кавычек).

##### Удаление нескольких событий #####
Команда удаляет все ранее добавленные события за указанную дату. Программа всегда должна выводить строку вида *«Deleted N events»*, где *N* — это количество всех найденных и удалённых событий. N может быть равно нулю, если в указанную дату не было ни одного события.

##### Поиск событий #####
Ищем и печатаем ранее добавленные события в указанную дату. Программа должна вывести на печать только сами события, по одному на строке. События должны быть отсортированы по возрастанию в порядке сравнения строк между собой (тип *string*).

##### Печать всех событий #####
С помощью этой команды можно показать полное содержимое нашей БД. Программа должна вывести на печать все пары: *Дата Событие* по одной на строке. Все пары должны быть отсортированы по дате, а события в рамках одной даты должны быть отсортированы по возрастанию в порядке сравнения строк между собой (тип *string*). Даты должны быть отформатированы специальным образом: *ГГГГ-ММ-ДД*, где *Г*, *М*, *Д* — это цифры чисел года, месяца и дня соответственно. Если какое-то число имеет меньше разрядов, то оно должно дополняться нулями, например, 0001-01-01 — первое января первого года.

##### Обработка ошибок ввода #####
Если пользователь ввёл неизвестную команду, то программа должна об этом сообщить, выведя строку *«Unknown command: COMMAND»*, где *COMMAND* — это та команда, которую ввёл пользователь. Командой считается первое слово в строке (до пробела).

Если пользователь ввёл дату в неверном формате там, где она ожидалась, то программа должна напечатать *«Wrong date format: DATE»*, где *DATE* — это то, что пользователь ввёл вместо даты (до пробела).

Если формат даты верный, но сама дата неверна, то программа должна напечатать более конкретную проблему:

* *«Month value is invalid: MONTH»*, где *MONTH* — это неверный номер месяца, например, 13 или 0.
* *«Day value is invalid: DAY»*, где *DAY* — это неверный номер дня в месяце, например, 39 или 0.
* Значение года проверять отдельно не нужно.
* Не нужно проверять календарную корректность даты: количество дней в каждом месяце считается равным 31, високосные года учитывать не нужно.
* Если неверны как месяц, так и день, то нужно вывести одно сообщение об ошибке в месяце.

После любой ошибки ввода и печати сообщения программа должна завершать своё выполнение.

##### Примеры #####

Корректный ввод: 
```objectivec
Add 0-1-2 event1
Add 1-2-3 event2
Find 0-1-2
Del 0-1-2
Print
```
Вывод:
```objectivec
event1
Deleted 1 events
0001-02-03 event2
```
Неверный формат даты:
```objectivec
Add 0-13-32 event1
```
Вывод:
```objectivec
Month value is invalid: 13
```


