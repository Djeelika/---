# Разработка алгоритма определения железнодорожной колеи и подвижного состава для предотвращения чрезвычайных ситуаций на железной дороге
Цифровой прорыв. Всероссийский Чемпионат 
https://hacks-ai.ru/championships/758453

Итоговую Сеть оставила на основе ResNet50 с заменой Классификатора.
Веса Модели ResNet50  были заморожены, обучала только Классификатор.
      Classifier = nn.Sequential(
        nn.Conv2d(2048, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False),
        nn.BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True),
        nn.ReLU(),
        nn.Dropout(p=0.1, inplace=False),
        nn.Conv2d(256, 4, kernel_size=(1, 1), stride=(1, 1))
      )

Краткое описание Итогового решения:
Для задачи классификации была использована
Предобученная модель ResNet50 с замороженными весами + свой Классификатор.
Классификатор состоит:
1. из одного сверточного слоя на 256 нейронов  с окном (3,3) без сворачивания и без нейрона смещения.
2. Нормализация
3. Отключение нейронов с вероятностью 10%
4. Выходной сверточный слой на 4 нейрона с окном (1,1)  без сворачивания.

Технические особенности:
Python ООП, torch, pickle , torchvision.transforms, PIL, Open CV

Уникальность:
Не проводила параллели и не искала схожесть.
Классификатор устанавливала сама в соответствии с Технической возможностью.


--------------------------------
Автоматизация функций управления и обеспечения безопасности за счет внедрения технических средств — всё это способы повышения уровня безопасности на железнодорожном транспорте.

Внедрение новой техники и технологий автоматизации позволяет исключить некоторые опасные технологические операции и значительно изменить характер работы многих работников железной дороги. Внедрение блоков определения препятствий на основе видеоаналитики позволяет вести дополнительный визуальный контроль пространства перед поездом, определять путь и направление движения. Применение камер различного диапазона видимости и фокусного расстояния увеличивает возможности системы технического зрения и превышает возможности человека по скорости реакции, дальности определения препятствий в том числе в сложных погодных условиях (ночь, дождь, снег, туман, задымленность, ослепление солнечным светом, переход из затемненных участков на освещенные).

Создание интеллектуальных систем, предупреждающих машиниста о возможном столкновении с потенциально опасными объектами, содержит в себе несколько первостепенных задач: определения колеи и подвижного состава. В рамках чемпионата требуется создать алгоритм, определяющий элементы дорожной инфраструктуры: колею (рельсошпальную решетку) и подвижной состав (локомотивы, грузовые вагоны, пассажирские вагоны).
