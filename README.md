# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #1 выполнил:
- Иргашев Тимофей Александрович
- РИ210944
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | # | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено

## Цель работы
Познакомиться с программными средствами для создания системы машинного обучения и ее интеграции в Unity.

## Задание 1
### Реализовать систему машинного обучения в связке Python - Google-Sheets – Unity.

![Снимок экрана (104)](https://user-images.githubusercontent.com/103359810/198316152-b4710378-7862-46e6-8304-7ad8459bfdcc.png)
![Снимок экрана (107)](https://user-images.githubusercontent.com/103359810/198316304-2e543bb5-2cfa-43c7-aba9-f2cb4627b55f.png)
![Снимок экрана (108)](https://user-images.githubusercontent.com/103359810/198316414-900519ad-a10d-4a2f-bd27-64187a6ccadb.png)
![Снимок экрана (109)](https://user-images.githubusercontent.com/103359810/198316534-88e1fb4a-618b-43fc-8691-5ee665f2719f.png)

Выводы: 
Чем больше шариков обучается одновременно, тем быстрее происходит обучение. 
Эффективность обучения увеличивается, когда одновременно обучается 3 шарика (по сравнению с одним) однако при дальнейшем увелечении числа агентов эффективность обучения не увеличивается. 
Чтобы агент с вероятностью больше 90% находил куб необходимо 3-4 итерации (по 10000 шагов). 
Со временем эффективность обучения падает. 
Если частота поподаний достаточно высокая (более 98%) она может начать падать (видно на 3 моделях). 

## Задание 2
### Подробно опишите каждую строку файла конфигурации нейронной сети.

###``` trainer_type: ppo ``` 
Используется стандартный тип тренировки Proximal Policy Optimization. У каждого типа есть уникальные свойства
``` batch_size: 10 ``` 
Количество опыта в каждой итерации
``` buffer_size: 100 ``` 
Количество опыта, которое необходимо собрать перед обновлением модели.
``` learning_rate: 3.0e-4 ``` 
Начальная скорость обучения. Обычно это значение следует уменьшать, если обучение нестабильно.
``` beta: 5.0e-4 ``` 
Параметр показывает количество случайных действий во время обучения.
``` epsilon: 0.2 ``` 
Влияет на то, насколько быстро может развиваться модель поведения во время обучения во время обучения.
``` lambd: 0.99 ``` 
Параметр указывает, насколько агент полагается на свою текущую оценку стоимости при вычислении обновленной оценки стоимости.
``` num_epoch: 3 ``` 
Количество проходов через буфер опыта при оптимизации градиентного спуска.
``` learning_rate_schedule: linear ``` 
Начальная скорость обучения для градиентного спуска. 
``` normalize: false ``` 
Применяется ли нормализация к входным данным векторного наблюдения.
``` hidden_units: 128 ``` 
Количество блоков в скрытых слоях нейронной сети. Для простых задач, где правильное действие представляет собой простую комбинацию входных данных наблюдения, это значение должно быть небольшим. 
``` num_layers: 2 ``` 
Количество скрытых слоев в нейронной сети. Для простых задач также рекомендуется небольшое значение.
``` gamma: 0.99 ``` 
Коэффициент дисконтирования для будущих вознаграждений, поступающих из окружающей среды. Со временем цена вознаграждения падает.
``` strength: 1.0 ``` 
Фактор, на который умножается вознаграждение, данное средой.
``` max_steps: 500000 ``` 
Максимальное число шагов, которое может быть сделано при обучении
``` time_horizon: 64 ``` 
Сколько шагов опыта нужно собрать каждому агенту, прежде чем добавить его в буфер опыта.
``` summary_freq: 10000 ``` 
Число шагов в одной итерации, после которых выводится статистика


## Задание 3
### Самостоятельно разработать сценарий воспроизведения звукового сопровождения в Unity в зависимости от изменения считанных данных в задании 2. 
Будем брать значения из переменной loss, так как она характеризует функцию потерь.
Будем воспроизводить "хорошую" реплику, если loss меньше 1000,
"Нормальную", если loss от 1000 до 2000
"Плохую", если loss от больше 2000
![100](https://user-images.githubusercontent.com/103359810/195175871-96a14b82-19ae-4cfe-b1c0-51b5925e6695.PNG)


