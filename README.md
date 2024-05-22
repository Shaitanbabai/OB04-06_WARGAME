# OB04-06_WARGAME
 **Развитие игры Герой-Монстр для уроков ОВ 04,05,06**


1. # **План проекта "Битва героя и монстра" по методологии Scrum (2 дня по 6 часов)**

## **Цель проекта:**

Создать консольную игру "Битва героя и монстра" на Python с использованием библиотеки pygame, 
текстовыми репликами героев и без звукового сопровождения.

### **Продолжительность:**

2 дня по 6 часов в день (12 часов в общем).

### **Команда:**

1 разработчик

### **Методология:**

Scrum (короткие спринты, ежедневные встречи, демонстрации).

### **Спринты:**

**День 1:**

**Спринт 1 (3 часа):**
Задача 1: Создание базовой структуры проекта (папки, файлы, импорты).
Задача 2: Реализация классов Hero и Monster (атрибуты, методы).
Задача 3: Написание кода для перемещения героя и монстра.
Спринт 2 (3 часа):
Задача 4: Реализация системы управления героем (перемещение, выбор оружия).
Задача 5: Реализация системы атак героя (контактная, дистанционная).
Задача 6: Реализация системы защиты героя (щит).

**Демонстрация:**
Продемонстрировать работу базовой механики игры: перемещение, атаки, защита.

**День 2:**

**Спринт 3 (3 часа):**
Задача 7: Реализация ИИ монстра (перемещение, атаки, защита).
Задача 8: Реализация системы реплик героев (загрузка, выбор, отображение).
Задача 9: Реализация системы проверки столкновений и нанесения урона.
Спринт 4 (3 часа):
Задача 10: Реализация системы условий победы и поражения.
Задача 11: Реализация меню управления (начать, сохранить, загрузить, выйти).
Задача 12: Доработка графического интерфейса (отображение информации, реплик).

**Демонстрация:**
Продемонстрировать финальную версию игры: все функции, реплики, меню.

### **Ежедневные встречи:**

* 15-минутные встречи в начале каждого рабочего дня.
* Обсуждение задач на день, прогресса, проблем.

### **Инструменты:**

* PyCharm (IDE)
* Git (система контроля версий)

### **Критерии завершения:**

* Все задачи в плане проекта выполнены.
* Игра полностью функциональна и соответствует описанию.
* Код хорошо структурирован, читаем и сопровождается комментариями.

### **Риски:**

* Недостаток опыта разработки игр.
* Неучтенные технические сложности.
* Ограниченное время на реализацию.

### **План действий при возникновении рисков:**

* Обсуждение проблем на ежедневных встречах.
* Поиск помощи/решений в интернете.
* Перераспределение задач и приоритетов.

### **Ожидаемые результаты:**

* Функционирующая консольная игра "Битва героя и монстра".
* Приобретение опыта разработки игр на Python.
* Понимание методологии Scrum.

2. # **Описание фнукциональности игры и игрового процесса** 

## **2.1. Графика и мультимедиа:**

Ограниченная графика с использованием статичных изображений .png монстра и героя.
Звук в игре не предусмотрен для упрощения.

**Графика для монстра (управляется компьютером)**
* два альтернативных (зеркальных) изображения в зависимости направления его движения по горизонтали
* изображение "Улыбка" при реализации функции защиты.

**Графика для героя (управляется человеком):**
* два изображения с разным оружием ("Меч", "Лук", "Щит")и два их зеркальных отражения, 
аналогично тому, как это реализовано для монстра.
* изображение "Щит" при реализации функции защиты

## **2.2. Управление:**

* В верхней панели игрового поля отображеются счетчики здоровья монстра и героя, а также 
  текстовые кнопки выбора средства атаки (оружия) и защиты Героя.
* Снизу отображаются текстовые кнопки управления игрой (Старт, Пауза, Сохранение, Загрузка и Выход)

**Скорость:**

* При 100% здоровья - базовая скорость перемещения героя и монстра (7).
* При потере каждых 20% здоровья скорость персонажа снижается на 20%.

### **2.2.1. Герой:**

**Перемещение с помощью мыши:**
При клике мыши герой плавно перемещается в указанную точку с базовой скоростью, если она не скорректирована
на остаток здоровья.

**Атака Героя:**

**Общее правило:** атаковать  доступным способом (монстр) или выбранным оружием (герой)
можно только находясь в пределах расстояния от внешней границы цели, разрешенного 
для соответствующего способа монстра или оружия героя.

Средство атаки героя - "Меч" и "Лук". 
Средство защиты героя - "Щит". 

Способы удара (атаки) и защиты, заивсят от выбора средств:
* контактный ("Меч") 
* дистанционный ("Лук")
* защита ("Щит")

Одновременно может использоваться только один из способов атаки или защиты.

**Контактный удар Героя** 

* Наносится "Меч" с расстояния 0-20  между ближайшими точками границы изображений монстра и героя.
* Удар наносится с помощью клика на левую кнопку мыши, при наведении курсора на монстра. 
* Удар осуществляется при выполнении условия о допустимом расстоянии от цели для выбранного способа атаки.
* Контактный удар Героя может наноситься с интервалом 1 раз в 4 секунды при соблюдении остальных условий.

Удар "Меч" дает 10% урона ( -10% от здоровья) монстру с вероятностью 50%.
При выборе средства "Меч" и контактного способа атаки для героя используется изображение Swordsman.

**Дистанционный удар Героя** 

* Наносится из "Лук" с расстояния 50-150 между ближайшими точками границы изображений монстра и героя.
* Удар наносится с помощью клика на левую кнопку мыши, при наведении курсора на монстра. 
* Удар осуществляется при выполнении условия о допустимом расстоянии от цели для выбранного способа атаки.

Выстрел из "Лук" дает 20% урона монстру с вероятностью 50%.
Герой может сделать не более 6 выстрелов из "Лук" в минуту.
При выборе средства "Лук" и дистанционного способа атаки для героя используется изображение Archer.

**Защита Героя:**

* Осуществляется при помощи средства "Щит". Исключает ущерб от атак монстра на расстоянии на расстоянии 0-75
между ближайшими точками границы изображений монстра и героя.
* Защита активируется игроком по нажатию кнопки "Щит" в меню.
* Действует 5 секунд с момента выбора средства "Щит".
* Выбор средства "Щит" не ограничивает перемещение Героя.
* При выборе средства "Щит" для героя используется изображение Shield.


### **2.2.2. Монстр**

Перемещение случайным образом с базовой скоростью, с поправкой на остаток здоровья (см. [п.2.2.]())
и расстояние до Героя (см. п. 2.____)

**Атака Монстра:**

**Общее правило:** атаковать  доступным способом (монстр) или выбранным оружием (герой)
можно только находясь в пределах расстояния от внешней границы цели, разрешенного 
для соответствующего способа монстра или оружия героя.

Средство атаки монстра - "Зубы" и "Огонь". 
Средство защиты монстра - "Улыбка". 

Способы удара (атаки) и защиты, заивсят от выбора средств:
* контактный ("Зубы") 
* дистанционный ("Огонь")
* защита ("Улыбка")

Одновременно может использоваться только один из способов атаки или защиты.

**Контактный удар Монстра**

* Наносится "Зубы" с расстояния 0-20  между ближайшими точками границы изображений монстра и героя.
* Удар осуществляется при выполнении условия о допустимом расстоянии от цели для выбранного способа атаки.
* Монстр наносит удар случайным образом при нахождении на разрешенном для этого типа удара 
диапазоне расстояний в течение 2 секунд (игрок имеет шанс отойти из зоны удара и сорвать атаку монстра)
* Контактный удар Монстра может наноситься с интервалом 1 раз в 4 секунды при соблюдении остальных условий.

Удар "Зубы" дает 10% урона герою с вероятностью 50%.
При выборе средства "ЗУбы" и контактного способа атаки для Монстра используется изображение Mםnster.

**Дистанционный удар Монстра** 

* Наносится из "Огонь" с расстояния 50-150 между ближайшими точками границы изображений монстра и героя. 
* Удар осуществляется при выполнении условия о допустимом расстоянии от цели для выбранного способа атаки.
* Монстр наносит удар случайным образом при нахождении на разрешенном для этого типа удара 
диапазоне расстояний в течение 2 секунд (игрок имеет шанс отойти из зоны удара и сорвать атаку монстра)
* Дистанционный удар Монстра может наноситься с интервалом 1 раз в 6 секунд при соблюдении остальных условий.

Выстрел из "Огонь" дает 10% урона герою с вероятностью 75%.
При выборе средства "Огонь" и дистанционного способа атаки для Монтсра используется изображение Monster.

**Защита Монстра:**

* Осуществляется при помощи средства "Улыбка". Исключает ущерб от атак героя на расстоянии на расстоянии 0-75
  между ближайшими точками границы изображений монстра и героя.
* Использование Монстром средства "Улыбка" возможно при остатке здоровья 10-50%.
* Активируется случайным образом с вероятностью 50% в диапазоне 50-150 пикселей от героя.
* "Улыбка" действует 3 секунды с момента активации и не ограничивает движение монстра.
* При выборе средства "Улыбка" для героя используется изображение Smile.

## **2.3. Игровой процесс**

### **2.3.1. Общее описание**

**Старт игры:**

* При запуске игры Монстр и Герой появляются в случайных координатах, но не менее чем 
в 300 пикселях друг от друга.
* Игра начинается через 6 секунд после запуска.

**Ход игры:**

* В ходе игры Герой, управляемый пользователем с помощью мыши, перемещается по игровому полю.
* Монстр перемещается случайным образом с базовой сокростью 7, оказавшись на расстоянии от Героя 150-50 
Монстр начинает движение к полученным координатам расположения героя со скоростью +30% к базовой. 
* Задача героя всеми способами и средствами атаки стремится нанести поражение Монстру (остаток здоровья 0%, 
отрицательный приравнивается к 0%).
* Монстр, управляемый компьютером, стремится к той же цели в отношении Героя. 
* Игровые действия Монстра и Героя сопровождаются репликами, случайно выбранными из списков, 
соответствующих комментируемому действию Монстра и Героя.

**Условия победы:**

Победа достигается в одном из двух случаев
* Нанесение 100% урона сопернику, при это расчетный остаток здоровья меньше 0% принравнивается к 0%.
* Отсутствие активности (перемещений, действий) Героя более 30 секунд - побеждает Монстр.

**Оповещения:**

* Автоматический обмен репликами монстра и героя при запуске игры.
* Отображение реплики атакующего и атакованного в момент атаки и в течение 2 секунд после.
* Отображение изображения Щита, либо Улыбки, в зависимости от того, кто победил,
и победной реплики героя/монстра после окончания игры.

**Пауза:**
Для прерывания игры можно использовать кнопку Пауза в нижнем меню, где находятся 
кнопки Старт, Сохранение, Загрузка и Выход.

Однократное нажатие кнопки "Пауза" прервывает игру, повторное запускает с того же места с задержкой в 2 секунды.

### **2.3.2. Реализация управления героем**

Использовать модуль pygame для отслеживания положения мыши и нажатий кнопок.

**При клике мыши:**
Получить координаты курсора мыши.
Рассчитать расстояние между героем и курсором мыши.

Если расстояние меньше 20 (контактная атака):
* Проверить, находится ли монстр в зоне атаки (0-20 пикселей).
* Если да, то нанести урон Монстру и отобразить реплику атаки героя.

Если расстояние между 50 и 150 пикселями (дистанционная атака):
* Проверить, находится ли монстр в зоне атаки (50-150 пикселей).
* Если да, то нанести урон монстру, отобразить реплику атаки Героя.

При нажатии кнопки "Щит" в меню:
* Активировать защиту героя (щит).
* Изменить текущее изображение героя (Swordsman или Archer) на Shield
* Прочие условия см. [в п.2.2.1. абзац "Защита Героя"]()

### **2.3.3. Реализация ИИ Монстра**

Использовать библиотеку random для генерации случайных чисел.

**Движение монстра:**
* В случайные моменты времени генерировать новое направление движения (влево, вправо, вверх, вниз).
* Программа перемещает Монстра в выбранном направлении с заданной скоростью 7.
* При потере каждых 20% здоровья скорость монстра снижается на 20%.
* Если монстр находится в диапазоне 50-150 (диапазон дистанционного удара "Огонь") от героя, 
то увеличить его скорость на 30% и направить по полученным координатам местонахождения героя.

**Атака монстра:**
Генерировать контактную или дистанционную атаку в соответствии с расстоянием до Героя (см. [п.2.2 "Монстр"]())

Если выбран контактный удар:
* Проверить, находится ли герой в зоне атаки (0-20 пикселей).
* Если да, то нанести урон Герою средством "Зубы", отобразить реплику атаки монстра.

Если выбрана дистанционная атака:
* Проверить, находится ли герой в зоне атаки (50-150 пикселей).
* Если да, то нанести урон герою, отобразить реплику атаки монстра.

Защита монстра ("Улыбка"):"
* "Улыка" может активироваться Монстром, если его здоровье монстра от 10 до 50%
* "Улыбка" активируется в случайные моменты времени при нахождении в диапазоне 50-150 
от героя (дальность дистанционного удара)
* Сделать монстра неуязвимым на 3 секунды.
* прочие условия из [п.2.2.2. Монстр, абзац Защита Монстра]().

### **2.3.4. Отображение информации**

* Использовать модуль pygame для рисования текста и элементов графического интерфейса (кнопок)
* Отображать счетчики остатка здоровья Монстра и Героя (в % от 100%) в верхнем меню.
* Отображать кнопки выбора оружия героя (меч, лук, щит) в нверхнем меню
* Отображать реплики монстра и героя в момент удара и получения ущерба в течение двух секунд после. 
* Отображать реплики ИМонстра и Героя при потере здоровья в внизу  игрового поля 
в 20 от грнаицы в порядке очередности реплик.
* Отображение реплик Героя и Монстра при атаке в верху игрового поля в 20 от грнаицы в порядке очередности реплик.

### **2.3.5. Звуковые эффекты**
НЕ ПРЕДУСМОТРЕНЫ
ПРи изменении решения - спользовать модуль pygame.mixer для воспроизведения звуковых эффектов.
Добавить звуки атак, защиты, урона и других действий.

## 2.4. Сохранение и загрузка игры:

Использовать модуль pickle для сохранения и загрузки данных игры.
Сохранять состояние игры (положение монстра и героя, их здоровье, выбранное оружие) в файл при нажатии 
на кнопку "Сохранить".
Загружать данные игры из файла при запуске игры или нажатии на кнопку "Загрузить".

## **2.5. Файловая структура:**

game/:
    data/:
        images/:
            hero/:
                SwordsmanLeft.png
                SwordsmanRight.png
                ArcherLeft.png
                ArcherRight.png
                Shield.png
            monster/:
                MonsterLeft.png
                MonsterRight.png
                Smile.png
        texts/:
            hero_greetings.txt
            hero_attack.txt
            hero_hurt.txt
            hero_defense.txt
            hero_win.txt
            monster_greetings.txt
            monster_attack.txt
            monster_hurt.txt
            monster_defense.txt
            monster_win.txt
    scripts/:
        game.py
        hero.py
        monster.py
        ui.py
README.md

## **2.6. Реплики:**

В папке data/texts будут созданы текстовые файлы с репликами героя и монстра для разных ситуаций:
* hero_greetings.txt - приветствие героя
* hero_attack.txt - атака героя
* hero_hurt.txt - получение урона героем
* hero_defense.txt - защита героя
* hero_win.txt - победа героя
* monster_greetings.txt - приветствие монстра
* monster_attack.txt - атака монстра
* monster_hurt.txt - получение урона монстром
* monster_defense.txt - защита монстра
* monster_win.txt - победа монстра

В файлах будут содержаться реплики, разделенные символом новой строки.

**Реализация реплик:**

* В модуле ui.py добавить функции для загрузки и обработки реплик.
* Функция load_replies(filename) будет загружать содержимое текстового файла с репликами в список.
* Функция get_random_reply(replies) будет случайным образом выбирать реплику из списка.

В модуле game.py использовать функции из ui.py для отображения реплик:

При запуске игры:
* Загрузить реплики приветствия для героя и монстра.
* Отобразить реплики на экране.

**В момент атаки и 2 секунды после:**
* Загрузить реплики атаки и получения урона для героя и монстра.
* Отобразить реплики на экране.

**При выборе защиты:**
* Загрузить реплики защиты для героя и монстра.
* Отобразить реплики на экране.

При достижении победы за счет достижения 0% здоровья одним из участников:
* Загрузить реплики победы для героя или монстра (в зависимости от исхода).
* Отобразить реплику на экране.