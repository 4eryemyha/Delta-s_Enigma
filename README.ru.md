### ⚠️ Обязательно для прочтения работодателям
#### Этот проект стал отправной точкой в моём изучении Unreal Engine и остаётся в разработке до сих пор. Изначально он задумывался не для коммерческой продажи, а как учебное пособие для освоения игрового движка. Со временем проект значительно изменился, так как в начале работы не было чётко продуманной архитектуры и плана. Проект ни к чему итоговому пока не пришёл, поэтому в этом описании я постараюсь подробно рассказать о том, чего я достиг в процессе его создания.



# Delta's Enigma

### Ссылка для скачивания (если применимо)
[Скачать проект](#) — ссылка на файлы проекта, если они имеют большой размер.

---



# Содержание

1. [Описание проекта](#описание-проекта)
2. [Дизайн UI/UX](#дизайн-uiux)
   1. [Философия дизайна](#философия-дизайна)
   2. [Обзор интерфейса пользователя](#обзор-интерфейса-пользователя)
   3. [Особенности пользовательского опыта](#особенности-пользовательского-опыта)
3. [Реализованные функции](#реализованные-функции)
   1. [Название функции 1](#название-функции-1)
   2. [Название функции 2](#название-функции-2)
4. [Дополнительные реализации](#дополнительные-реализации)
   1. [Дополнительный аспект 1](#дополнительный-аспект-1)
   2. [Дополнительный аспект 2](#дополнительный-аспект-2)

---



# Описание проекта

«Delta's Enigma» — это приключенческая игра с элементами выживания, где игрокам предстоит исследовать таинственный мир, решать сложные головоломки, добывать ресурсы и противостоять опасностям. Каждый шаг в игре открывает новые тайны и ставит перед игроком всё более сложные задачи.

---



# Дизайн UI/UX

### Дизайн

Дизайн интерфейса был полностью разработан в Figma. Основная идея заключается в минимализме: я отказался от изображений в пользу текстового отображения, придавая интерфейсу вид, напоминающий код.

![Изображение интерфейса](путь_к_изображению)

**Ключевые особенности:**
- Цветовой гаммной были выбранны холодные цвета, более напоминающие голографический интерфейс
- Весь интерфейс не должен занимать много места, игрок должен по большей частью наслаждаться визуалом

### Модульные виджеты

Весь интерфейс был реализован с помощью модульных виджетов. Модульный виджет представляет собой элемент, созданный со встроенными настройками для отображения визуала (например, анимации) и логики, с возможностью полной кастомизации при создании интерфейса. Я выбрал модульные виджеты, чтобы сократить время, затрачиваемое на разработку интерфейса, и их использование значительно ускорило процесс.

![Изображение интерфейса](путь_к_изображению)

---



# Реализованные функции


###  Player character

Изначально был создан персонаж для исследования мира и взаимодействия с ним. Основные возможности включают в себя: передвижение, инвентарь, взаимодействия и систему жизнеобеспечения.

![Изображение функции 1](путь_к_изображению)


### interactable objects (Physics)

Для большинства взаимодействий в игре требовались объекты, подчиняющиеся законам физики, с которыми можно было взаимодействовать: подбирать, бросать, вставлять куда-либо и так далее. Для этого был создан Parent-объект, содержащий всю логику взаимодействий. Затем на основе этого Parent-объекта создавались дочерние объекты, в которых нужно было изменить всего несколько параметров, чтобы указать, что это за объекты и как персонаж может с ними взаимодействовать.

![Изображение функции 2](путь_к_изображению)


### landscape - материал

Затем возникла необходимость создать большой открытый мир. Для этого был использован ландшафт (landscape) и процедурный материал, который настраивался для создания различных биомов и процедурного появления небольших объектов.

![Изображение функции 2](путь_к_изображению)


### Существа и Процедурная анимация

Для оживления мира была необходима разнообразная фауна. Были созданы два типа существ: пауки и летающие драконы. Основой анимации для обоих видов стала процедурная анимация. У драконов каждая часть тела следует за предыдущей, создавая эффект извивающегося змеиного тела. У пауков была реализована процедурная анимация по костям (IK), которая позволяет им адаптироваться к поверхностям и двигаться в зависимости от положения ног. Это делает их движения более реалистичными и схожими с движениями реальных аналогов.

![Изображение функции 2](путь_к_изображению)


### Добыча минералов с помощью буда

Одной из ключевых механик игры является добыча ресурсов. Она реализована с помощью бура, который вызывается на месторождения минералов. Сначала игрок должен найти подходящее место, затем вызвать бур. После прибытия бур начинает раскопки, а по их завершению звучит характерный звук, и из бура вылетает бочка с добытым минералом.

![Изображение функции 2](путь_к_изображению)


### Система крафта

Для создания предметов была реализована функция крафта. В процессе добавлен визуальный эффект (FVX): при распаде элементов для крафта они не только красиво исчезают, но и оставляют за собой частицы, которые затем всасываются в трубу.

![Изображение функции 2](путь_к_изображению)


### Система изучения

Система исследований была реализована с помощью древа технологий. Каждый элемент становится доступен только после открытия предыдущих. Для изучения конкретного элемента требуется сначала исследовать соответствующий предмет в лаборатории.

![Изображение функции 2](путь_к_изображению)


### Система базы и кислорода

По задумке у игрока должна быть база, где он может жить и развиваться. Для этого были созданы различные части базы, которые можно комбинировать, чтобы собрать полноценную. Так же на базе создана система кислорода, которая тратит его из внутреннего хранилища.

![Изображение функции 2](путь_к_изображению)


### Машины

Для полноценного иследования открытого мира были созданы машины. Реализованны они через физическое взаимодействие, а не через кости.

![Изображение функции 2](путь_к_изображению)


---



# Дополнительные реализации

###  VFX эфекты

Созданы различные VFX эффект. При создании использовалась не только работа с материалами, но и с 3D партиклами.



### Cell Shader

Cell Shader - это графический шейдер, который полностью уберал световой градиент цветов и отображал только определённые настраиваемые слои. Слои разделяются в зависимости от количества попадаемого света.

---

