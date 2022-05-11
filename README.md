# Todo list

![TodoListAnimation](https://user-images.githubusercontent.com/35418986/167744145-4348b540-3a29-4b6c-8826-a2110ac3db94.gif)

### Описание 

В данном задании вам нужно реализовать свой список задач как минимум со следующим функционалом:
1) Должна быть реализована возможность добавлять, редактировать (внутри таблицы) и выполнять задачи (нажатием на чек бокс).
2) Строка с выполненной задачей должна изменять свой цвет на зелёный.
3) Должна быть реализована возможность сортировки задач.
4) Должен использоваться model/view подход. То бишь информация о задачах должна храниться в модели и предаваться во вью через интерфейс.

В качестве иллюстрации предоставлены gif и установочник к рабочей версии программы. Вид вашей реализации может отличаться.

После выполнения задания файлы проекта нужно выложить в ваш репозиторий на GitHub.

### Дополнительная информация

1) В качестве базовой модели в данном случае лучше использовать QAbstractTableModel.
2) Кроме уже известных вам методов нужно будет перегрузить ещё `setData`, `headerData`, `insertRows`, `flags`. 
Перегружать методы можно нажатием alt+enter на базовый класс и выбором `Insert Virtual Functions of Base Classes` (в таком случае 
они сразу будут иметь правильную сигнатуру и вам останется их только реализовать).
4) Для добавления строки в таблицу у модели должен вызываться метод `insertRows`. Почитать про его использование можно, например, 
[здесь](https://doc.qt.io/qt-5/model-view-programming.html#inserting-and-removing-rows).
4) Для изменения заголовков у столбцов используйте метод `headerData`. Почитать можно
[здесь](https://doc.qt.io/qt-5/model-view-programming.html#model-headers-and-data).
5) Для добавления возможности редактировать ячейки таблицы используйте методы `setData` и `flags`. В методе `flags` для нужных 
индексов нужно в возвращаемую битовую маску добавить Qt::ItemIsEditable. В методе `setData` для роли `Qt::EditRole` меняйте значение 
в вашей структуре данных (в которой хранятся задачи, например, векторе) в соответствии с полученным QVariant value. Не забудьте выбросить сигнал dataChanged. 
Подробнее почитать можно [здесь](https://doc.qt.io/qt-5/modelview.html#2-5-the-minimal-editing-example)
6) Для реализации чек бокса в методе `flags` для необходимого столбца добавьте флаг `Qt::ItemIsUserCheckable`. В функции `setData` обрабатывайте 
роль `Qt::CheckStateRole`.
7) Для реализации изменения цвета строки выполненной задачи в методе `data` обрабатывайте роль `Qt::BackgroundRole`.

Про роли дополнительно почитать можно [здесь](https://doc.qt.io/qt-5/model-view-programming.html#item-roles).
