---
lab:
  title: Лабораторная работа 4. Создание автоматизированного решения
  module: 'Module 4: Get Started with Power Automate'
---

# <a name="lab-4-how-to-build-an-automated-solution"></a>Лабораторная работа 4. Создание автоматизированного решения

## <a name="scenario"></a>Сценарий

Bellows College is an educational organization with multiple buildings on campus. Campus visitors are currently recorded in paper journals. The information is not captured consistently, and there are no means to collect and analyze data about the visits across the entire campus.

Администрация кампуса хотела бы модернизировать систему регистрации посетителей таким образом, чтобы допуск в здания контролировали сотрудники службы безопасности, а обитатели кампуса предварительно регистрировали все визиты и обязательно записывали их.

В этом курсе обучения вы разработаете приложения и реализуете автоматические процедуры, позволяющие администрации и службе охраны Bellows College контролировать доступ в здания кампуса.

В этом задании вы создадите поток Power Automate для отправки электронной почты посетителю при назначении визита.

## <a name="high-level-lab-steps"></a>Обзор этапов работы над общим заданием

Для выполнения проекта необходимо выполнить следующие требования.

- При назначении визита контактные лица должны получать уведомления по электронной почте.

## <a name="prerequisites"></a>Предварительные требования

- Выполнить **задание 0 модуля 0 «Проверка лабораторной среды»** .
- Выполнить **задание 1 модуля 2 "Моделирование данных"** .
- Выполнить **задание 3 модуля 2 "Создание приложения на основе модели"** .
- Должно быть создано контактное лицо "Александр Демидов" с заполненным адресом электронной почты.

## <a name="exercise-1-create-visit-notification-flow"></a>Упражнение 1. Создание потока уведомлений о визитах

<bpt id="p1">**</bpt>Objective:<ept id="p1">**</ept> In this exercise, you will create a Power Automate flow that implements the requirement. The visitor should be sent an email that includes the unique code assigned to the visit when a visit is created.

### <a name="task-1-create-a-flow"></a>Задача \#1. Создание потока

1.  Navigate to <ph id="ph1">&lt;https://make.powerapps.com&gt;</ph>. You may need to reauthenticate - click <bpt id="p1">**</bpt>Sign in<ept id="p1">**</ept> and follow instructions if needed.

2.  В правом верхнем углу экрана выберите свою среду **[ваши инициалы] практика** (если она еще не выбрана).

3.  В левой области навигации щелкните **Потоки**.

4.  При появлении запроса выберите **Начало работы**.

5.  Щелкните **Создать поток** и выберите **Автоматизированный облачный поток**.

6.  Введите "Уведомление о визите"в поле **Имя потока**.

7.  В разделе **Выбор триггера потока** найдите **Dataverse**.

8.  Выберите триггер **При добавлении, изменении или удалении строки**, а затем нажмите кнопку **Создать**.

9.  Укажите условия триггера для потока, как показано ниже.

    1.  Выберите **Добавлено** для параметра **Тип изменения**

    2.  В поле **Имя таблицы** выберите **Визиты**.

    3.  В поле **Область действия** выберите **Организация**.

    4.  On the trigger step, click the ellipsis (<bpt id="p1">**</bpt>...<ept id="p1">**</ept>) and click <bpt id="p2">**</bpt>Rename<ept id="p2">**</ept>. Rename this trigger <bpt id="p1">**</bpt>"When a visit is added"<ept id="p1">**</ept>. This is a good practice, so you and other flow editors can understand the purpose of the step without having to dive into the details.

### <a name="task-2-create-a-step-to-get-the-visitor-row"></a>Задача \#2. Создание шага для получения строки посетителя

1.  Bellows College — образовательное учреждение, имеющее на территории своего кампуса несколько зданий.

2.  Найдите **Dataverse**.

3.  Выберите действие **Выбрать строку по идентификатору**.

4.  В поле **Имя таблицы** введите **Контакты**.

5.  Сейчас для регистрации посетителей кампуса используются бумажные журналы.

6.  Информация собирается несогласованно, отсутствуют средства сбора и анализа данных о визитах по всему кампусу.

7.  On this action, click the ellipsis (<bpt id="p1">**</bpt>...<ept id="p1">**</ept>) and click <bpt id="p2">**</bpt>Rename<ept id="p2">**</ept>.
        Rename this action <bpt id="p1">**</bpt>"Get the Visitor"<ept id="p1">**</ept>. This is a good practice, so you and other flow editors can understand the purpose of the step without having to dive into the details.

### <a name="task-3-create-a-step-to-send-an-email-to-the-visitor"></a>Задача \#3. Создание шага для отправки посетителю электронного письма

1.  Click <bpt id="p1">**</bpt>+ New step<ept id="p1">**</ept>. This is the step that will send an email to the visitor.

2.  Выполните поиск слова *почта*, выберите соединитель **Office 365 Outlook** и действие **Отправить по электронной почте (V2)** .

3.  Если появится запрос на принятие условий использования этого действия, щелкните **Принять**.

4.  В поле **Кому** выберите **Добавить динамическое содержимое**. 
    
5.  Выберите значение **Электронная почта** из списка динамического содержимого.
        > Notice that it is beneath the **Get the visitor** header. This means you
        are selecting the Email that is related to the Visitor that you looked
        up in the previous step.

6.  В поле **Тема** введите строку **Ваш запланированный визит в Bellows College**.

7.  В поле **Содержимое электронного письма** введите следующее:

>   Dynamic content needs to be placed where fields are named in brackets. It is recommended to copy &amp; paste all text first and then add dynamic content in the correct places.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
   Dear {First Name},

   You are currently scheduled to visit Bellows Campus from {Scheduled Start} until {Scheduled End}.

   Best regards,

   Campus Administration
   Bellows College
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

8.  Highlight the <bpt id="p1">**</bpt>{First Name}<ept id="p1">**</ept> text. Replace it with the <bpt id="p1">**</bpt>First Name<ept id="p1">**</ept> field from the <bpt id="p2">**</bpt>Get the Visitor<ept id="p2">**</ept> step.

9.  Highlight the <bpt id="p1">**</bpt>{Scheduled Start}<ept id="p1">**</ept> text. Replace it with the <bpt id="p1">**</bpt>Scheduled Start<ept id="p1">**</ept> field <bpt id="p2">**</bpt>When a visit is added<ept id="p2">**</ept> step.

10.  Highlight the <bpt id="p1">**</bpt>{Scheduled End}<ept id="p1">**</ept> text. Replace it with the <bpt id="p1">**</bpt>Scheduled End<ept id="p1">**</ept> field from the <bpt id="p2">**</bpt>When a visit is added<ept id="p2">**</ept> step.

11.  Выберите команду **Сохранить**.

Leave this flow tab open for the next task. You flow should look approximately like the following:

![Пример шагов потока.](media/4-Flow.png)

### <a name="task-4-validate-and-test-the-flow"></a>Задача \#4. Проверка и тестирование потока

1.  Откройте новую вкладку в браузере и перейдите по адресу <https://make.powerapps.com>.

2.  В правом верхнем углу экрана выберите свою среду **[ваши инициалы] практика** (если она еще не выбрана).

3.  Щелкните **Приложения** и выберите приложение **Управление кампусом Bellows**, созданное ранее на основе модели.

3.  Оставив эту вкладку браузера открытой, вернитесь к предыдущей вкладке с вашим потоком.

4.  On the command bar, click <bpt id="p1">**</bpt>Test<ept id="p1">**</ept>. Select <bpt id="p1">**</bpt>Manually<ept id="p1">**</ept> and then click <bpt id="p2">**</bpt>Test<ept id="p2">**</ept>.

5.  Перейдите на вкладку браузера с открытым приложением на основе модели. 

6.  Используя навигацию в левой части экрана, выберите **Визиты**.

6. Нажмите кнопку **+Создать**, чтобы добавить новую запись **Визит**.

7. Заполните запись «Визит» следующим образом:

    -   **Имя**. Тестовый визит

    -   **Посетитель**. Александр Демидов

    -   **Запланированное начало**. Завтра в 8:00

    -   **Запланированное окончание**. Завтра в 9:00

8. Нажмите кнопку **Сохранить и закрыть**.

9. Navigate to the browser tab with your flow test running. After a short delay, you should see the flow running. This is where you can catch any issues in the flow or confirm that it ran successfully.

After a short delay, you should see an email in your inbox, since you populated John Doe's email as your personal email. Note that it may go to your Junk Email folder.

## <a name="challenges"></a>Сложности

- Play around with the formatting on the email. How can you make it more professional looking?