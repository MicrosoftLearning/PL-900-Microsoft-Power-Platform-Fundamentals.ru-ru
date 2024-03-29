---
lab:
  title: "Задание\_1. Моделирование данных"
  module: 'Module 2: Introduction to Microsoft Dataverse'
---

# Задание 1. Моделирование данных

**Арендаторы WWL: условия использования.** Если вам предоставляется арендатор в рамках обучения под руководством инструктора, обратите внимание, что арендатор предоставляется для поддержки практических занятий в ходе такого обучения. Арендаторы не должны использоваться совместно или для целей, выходящих за рамки практических занятий. Клиент, используемый в этом курсе, является пробным клиентом и не может использоваться или получить доступ после завершения класса и не имеет права на расширение. Клиентов нельзя переводить на платную подписку. Арендаторы, полученные в рамках этого курса, остаются собственностью корпорации Майкрософт, мы оставляем за собой право получить доступ к ним и вернуть их в любое время. 

## Сценарий

Колледж Bellows является образовательной организацией с несколькими кампусами и программами. Многие преподаватели и администраторы колледжей Беллоу должны посещать мероприятия, а также приобретать предметы. Исторически отслеживание этих расходов было проблемой. 

Администрация кампуса хотела бы модернизировать свою систему отчетности о расходах, предоставив сотрудникам цифровой способ сообщать о расходах. 

На протяжении всего этого курса вы создадите приложения и выполните автоматизацию, чтобы сотрудники Колледжа Bellows могли управлять расходами.

В этом задании вы создадите модель данных для поддержки следующих требований:

- R1 — сведения об отслеживании запланированных визитов в кампус.

- R2 — запись основных сведений для идентификации и отслеживания посетителей.

- R3 — планирование, запись и управление визитами.

Наконец, вы импортируете примеры данных в Microsoft Dataverse.

## Основные пошаговые действия для выполнения задания

Чтобы подготовить среды обучения, понадобится выполнить указанные ниже действия.

- Описание метаданных (таблиц и связей) см. в [документе модели данных](https://github.com/MicrosoftLearning/PL-900-Microsoft-Power-Platform-Fundamentals/blob/master/Allfiles/Campus Management.png). Чтобы открыть документ модели данных в новом окне, можно щелкнуть ссылку левой кнопкой мыши, удерживая клавишу CTRL, или щелкнуть ее правой кнопкой мыши.

- Создание таблицы "Расходы"

- Добавьте некоторые примеры данных. 

### Необходимые компоненты

- Завершение модуля 1 Lab 0 — проверка лабораторной **среды**

Аспекты, которые следует учитывать перед началом работы

- Соглашения об именовании — тщательно введите имена.

## Упражнение 1. Создание таблицы

**Цель.** В этом упражнении вы создадите новую пользовательскую таблицу для расходов.

### Задача #1. Создание таблицы расходов и столбцов

В **таблице "Расходы" содержатся сведения об отдельных расходах** , которые сотрудник может отправлять, включая причину, тип, дату и сумму.

1. Войдите в https://make.powerapps.com (если вход еще не выполнен)

1. **В меню "Среда"** в правом верхнем углу убедитесь, что **выбрана среда Dev One**.

1. На панели навигации слева выберите **Таблицы**.

1. Выберите **+ Создать таблицу** и **Задать дополнительные свойства**.

1. В **поле "Отображаемое имя"** введите "Расходы"

1. Выберите **Сохранить**.

1. В разделе **Схема** выберите **Столбцы**.

### Создание столбца "Дата расходов"

1. Выберите **+ Создать столбец**.

1. Введите дату расходов для **отображаемого имени**.

1. Выберите **"Дата только** для **типа** данных".

1. Измените значение **Обязательно** на **Обязательно для бизнеса**.

1. Разверните раздел **Расширенные параметры**.

1. В **корректировке** часового пояса выберите **"Только** дата".

    >**Примечание.** Мы используем **только поведение даты для** записи сведений о дате, так как дата посещения не должна изменяться при просмотре из другого часового пояса.

1. Выберите **Сохранить**.

### Создание столбца типа затрат

1. Выберите **+ Создать столбец**.

1. Введите тип расходов для **отображаемого имени**.

1. Выберите **вариант** для **типа** данных.

1. В поле **"Обязательный"** выберите **"Необязательно**".

1. Настройка **синхронизации с глобальным выбором **** "Да" (рекомендуется)**

1. В **разделе "Синхронизация" с** полем выберите **"Тип** расходов".

1. **Задайте для поля выбора** по умолчанию значение **None**.

1. Выберите **Сохранить**.

### Создание столбца назначения расходов

1. Выберите **+ Создать столбец**.

1. Введите назначение расходов для **отображаемого имени**.

1. Выберите **вариант** для **типа** данных.

1. В поле **"Обязательный"** выберите **"Необязательно**".

1. Настройка **синхронизации с глобальным выбором **** "Да" (рекомендуется)**

1. В **разделе "Синхронизация" с** полем выберите **"Назначение** расходов".

1. **Задайте для поля Default** значение **None**.

1. Выберите **Сохранить**.

### Создание столбца описания элементов

1. Выберите **+ Создать столбец**.

1. Введите описание элемента для **отображаемого имени**.

1. Выберите **несколько строк обычного текста &gt;** для **типа** данных.

1. Выберите **Сохранить**.

### Создание столбца "Сумма расходов"

1. Выберите **+ Создать столбец**.

1. Введите сумму расходов для **отображаемого имени**.

1. Выберите **валюту** для **типа** данных.

1. Выберите **Сохранить**.

 
## Упражнение 2. Ввод данных

**Цель.** В этом упражнении вы вручную вводите некоторые примеры данных в новую таблицу. 

### Задача #1. Изменение отображаемых столбцов

1. Если вход еще не выполнен, войдите в систему. https://make.powerapps.com

1. **Выберите среду Dev One** в правом верхнем углу, если она еще не выбрана.

1. На панели навигации слева выберите **Таблицы**.

1. Откройте таблицу **Expense** , созданную в предыдущем упражнении.

1. Рядом с столбцом **"Имя"** выберите **+26 больше**.

1. В появившемся меню выберите следующие столбцы.

    1. Дата расходов

    2. Назначение расходов 

    3. Тип расходов

    4. Сумма расходов

    5. Описание элемента

1. Выберите кнопку **Сохранить**.

## Задача #2. Добавление образца записи.

1. Щелкните стрелку** рядом с элементом ****"Изменить**". В появившемся меню выберите **"Изменить" на новой вкладке**.

1. В столбце **"Имя"** введите **Джон Doe**.

1. В столбце **"Дата** расходов" введите **xxx**.

1. В разделе **"Назначение** расходов" выберите **"Конференция**".

1. В столбце **"Тип** расходов" выберите **"Путешествия**".

1. В столбце **"Сумма расходов"** введите **750.00**.

1. В описании **элемента** введите короткое описание.

1. Нажмите кнопку TAB, чтобы перейти к следующей строке и **сохранить** запись.

Поздравляем, вы успешно создали новую таблицу и добавили данные.


