---
lab:
  title: "Задание\_1. Моделирование данных"
  module: 'Module 2: Identify foundational components of Microsoft Power Platform'
---

# Задание 1. Моделирование данных

**Арендаторы WWL: условия использования.** Если вам предоставляется арендатор в рамках обучения под руководством инструктора, обратите внимание, что арендатор предоставляется для поддержки практических занятий в ходе такого обучения. Арендаторы не должны использоваться совместно или для целей, выходящих за рамки практических занятий. Клиент, используемый в этом курсе, является пробным клиентом. Его нельзя использовать или получить к нему доступ после окончания курса, а также он не подлежит продлению. Клиентов нельзя переводить на платную подписку. Арендаторы, полученные в рамках этого курса, остаются собственностью корпорации Майкрософт, мы оставляем за собой право получить доступ к ним и вернуть их в любое время. 

## Сценарий

Bellows College — это образовательное учреждение с несколькими кампусами и программами. Многие преподаватели и администраторы Bellow College должны посещать мероприятия и приобретать товары. Исторически отслеживание таких расходов было сложной задачей. 

Администрация кампуса хотела бы модернизировать свою систему отчетности о расходах, предоставив сотрудникам цифровой способ уведомления о расходах. 

В рамках этого курса вы создадите приложения и выполните автоматизацию, чтобы сотрудники Bellows College могли управлять расходами.

Наконец, вы импортируете примеры данных в Microsoft Dataverse.

## Основные пошаговые действия для выполнения задания

Чтобы подготовить среды обучения, понадобится выполнить указанные ниже действия.

- Создать таблицу "Расходы"

- Добавить некоторые примеры данных. 

### Необходимые компоненты

- Выполнение **задания 0 модуля 1 "Проверка лабораторной среды"**

Аспекты, которые следует учитывать перед началом работы

- Соглашения об именовании — имена следует вводить внимательно.

## Упражнение 1. Создание таблицы

**Задача:** В этом упражнении вы создадите пользовательскую таблицу расходов.

### Задача 1. Создание таблицы и столбцов расходов

В таблице **Расходы** будут содержатся сведения об отдельных расходах, которые сотрудник может отправлять, включая причину, тип, дату и сумму.

1. Войдите в https://make.powerapps.com (если вход еще не выполнен)

1. В меню **Среда** в правом верхнем углу выберите среду **Dev One**.

1. На панели навигации слева выберите **Таблицы**.

1. Выберите **+Создать таблицу** и выберите **таблицу (расширенные свойства)** в раскрывающемся меню.

1. В поле **Отображаемое имя** введите `Expense`

1. Выберите **Сохранить**.

1. В разделе **Схема** выберите **Столбцы**.

### Создание столбца даты расходов

1. Выберите **+ Создать столбец**.

1. Введите `Expense Date` в качестве **отображаемого имени**.

1. В поле **Тип данных** выберите **Только дата**.

1. Измените значение **Обязательно** на **Обязательно для бизнеса**.

1. Разверните раздел **Расширенные параметры**.

1. В **корректировке** часового пояса выберите **только** дату.

    >**Примечание**. Мы используем поведение **Только дата** для записи сведений о дате, так как дата расходов не должна изменяться при просмотре из другого часового пояса.

1. Выберите **Сохранить**.

### Создание столбца типа расходов

1. Выберите **+ Создать столбец**.

1. Введите `Expense Type` в качестве **отображаемого имени**.

1. Выберите **Вариант** в поле **Тип данных**.

1. В поле **Обязательно** выберите **Необязательно**.

1. Настройка **синхронизации с глобальным выбором **** "Да" (рекомендуется)**

1. В поле **Синхронизировать этот вариант с** выберите **Тип расходов**.

1. Настройте для поля **Вариант по умолчанию** значение **Нет**.

1. Выберите **Сохранить**.

### Создание столбца назначения расходов

1. Выберите **+ Создать столбец**.

1. Введите `Expense Purpose` в качестве **отображаемого имени**.

1. Выберите **Вариант** в поле **Тип данных**.

1. В поле **Обязательно** выберите **Необязательно**.

1. Настройка **синхронизации с глобальным выбором **** "Да" (рекомендуется)**

1. В поле **Синхронизировать этот вариант с** выберите **Назначение расходов**.

1. Настройте для поля **Вариант по умолчанию** значение **Нет**.

1. Выберите **Сохранить**.

### Создание столбца описания элемента

1. Выберите **+ Создать столбец**.

1. Введите `Item Description` в качестве **отображаемого имени**.

1. Выберите **Несколько строк текста &gt; Обычный текст** для параметра **Тип данных**.

1. Выберите **Сохранить**.

### Создание столбца суммы расходов

1. Выберите **+ Создать столбец**.

1. Введите `Expense Amount` в качестве **отображаемого имени**.

1. Выберите **Валюта** для поля **Тип данных**.

1. Выберите **Сохранить**.

 
## Упражнение 2. Ввод данных

**Задача:** В этом упражнении вы вручную введете некоторые примеры данных в новую таблицу. 

### Задача 1. Изменение отображаемых столбцов

1. Если вы еще не выполнили вход, войдите в https://make.powerapps.com

1. В правом верхнем углу экрана выберите среду **Dev One** (если она еще не выбрана).

1. На панели навигации слева выберите **Таблицы**.

1. Откройте таблицу **Расходы**, созданную в предыдущем упражнении.

1. Рядом со столбцом **Имя** выберите **Еще 26**.

1. В появившемся меню выберите следующие столбцы.

    1. Дата расходов

    2. Назначение расходов 

    3. Тип расходов

    4. Сумма расходов

    5. Описание элемента

1. Выберите кнопку **Сохранить**.

## Задача 2. Добавление примера записи.

1. Щелкните **стрелку** рядом с элементом **Изменить**. В появившемся меню выберите **Изменить на новой вкладке**.

1. В столбце **"Имя"** введите `John Doe`.

1. В столбце **Дата расходов** введите **xxx**.

1. В столбце **Назначение расходов** выберите **Конференция**.

1. В столбце **Тип расходов** выберите **Поездка**.

1. В столбце **"Сумма расходов"** введите `750.00`.

1. В поле **Описание элемента** введите короткое описание.

1. Нажмите кнопку TAB, чтобы перейти к следующей строке и **сохранить** запись.

Поздравляем, вы успешно создали таблицу и добавили данные.


