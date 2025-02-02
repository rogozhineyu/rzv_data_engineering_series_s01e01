# rzv_de_series_s01e01

![Main cover](./images/s01e01.jpg)

## 📽️ Добро пожаловать на курс!
Перед тобой открытый эпизод учебного курса rzv Data engineering series. Выбери, какой сериал ты включишь сегодня вечером -- тот, который отвлечёт тебя от жизни, или тот, который даст возможность освоить навыки и творить!

Курс проходит в self-paced формате, инфраструктура разворачивается локально в Docker контейнерах. Ожидаю, что материалы для ответов на возникающие вопросы будешь искать самостоятельно и обсуждать в [общем чате](https://t.me/rzv_de_series). К задачам прикладывается решение на уровень Middle. Задания разделены на разные уровни сложности. Начни с того, где будешь ощущать себя наиболее комфортно, и двигайся наверх. Чем выше грейд, тем абстрактнее постановка задачи -- тут как в жизни.

Навыки, которые ты приобретаешь на курсе, можно практически без потерь перенести на рабочую практику. И, в отличие от большинства курсов, здесь ты работаешь с "живыми" данными, которые генерируются в реальном времени (хоть и упрощённо). К концу первого сезона сериала ты сможешь на практике прочувствовать дата-инженерные проблемы и написать их решения своими руками.

Чем дальше по курсу, тем больше модулей будет подключаться вслед за "развитием бизнеса":
* забор данных из локального сервиса API
* построение витрин данных и BI-дашбордов
* миграция ETL с Pandas на Spark
* интеграция Data Quality инструментов
* много чего ещё

## 🥱 Кратко
1. Сделай fork репозитория и склонируй его на компьютер
2. Установи docker desktop
3. Следуй шагам из [подключения к базам и настройки инфраструктуры](setup_instructions_ru.md)
4. Выбери G0_Trainee, чтобы запустить уже готовое решение и посмотреть на его работу. Последовательно проходи грейды с G1, чтобы освоить загрузку данных через Airflow

## 🎬 Что в программе сегодня
Это первый эпизод, раскрывающий особенности инкрементальной загрузки через Apache Airflow. В процессе выполнения задач на уровне Middle и Senior ты столкнёшься со многими трудностями, которые есть и в реальной рабочей практике. При этом, даже Junior и Intern познакомят тебя с новыми концепциями и постепенно подготовят к более сложным задачам. 

Призываю сначала попробовать решить задачу самостоятельно, а потом смотреть мой вариант.

Ты изучишь:
* инкрементальную загрузку данных с использованием Airflow
* базовый ETL через Pandas
* работу с реляционными базами данных через SQL и Python
* установку соединений к источникам через Airflow и pgAdmin4
* запуск приложений в контейнерах через Docker Compose

## 🎞️ В ролях
![Stack used](./images/image-6.png)

* Python 3.10
* Postgres 15 (DWH)
* Pandas 2.1.4 (ETL)
* Apache Airflow 2.7.3 (Orchestrator)
* pgAdmin4 (DBMS client)
* Docker

## 👨🏻‍🦲 👦🏻 🧔🏻 Сценарии заданий и грейды
Для каждого уровня создана своя директория. С каждым грейдом я уменьшаю количество готового кода и усложняю задачу. Содержимое директорий немного отличается, но инфраструктура везде готова к использованию. Детальные задания описаны в ```README.md``` каждого грейда. Выбери свой и не стесняйся снизить уровень, если нужно.

**Trainee**: Весь код уже реализован и решает задачу middle. Просто запусти и изучи. Там же расписал, почему я написал код именно так.

**Intern**: Дополни существующую конфигурацию, чтобы написанный DAG начал грузить данные из нового источника и по новым таблицам. Напиши простой даг работы с файловой системой через BashOperator.

**Junior**: Напиши инкрементальную загрузку без учёта историчности. Данные на источнике не обновляются.

**Middle**: Напиши инкрементальную загрузку в таблицы SCD2. Учти, что данные могут обновляться на источнике.

**Senior**: Сценарий как для Middle + настрой Write-Audit-Publish паттерн для обеспечения качества данных и проведи нагрузочное тестирование написанного решения.


## Галерея
Историческое хранение данных с SCD2:
![Historical storage with SCD2](./images/image.png)

Инкрементальная загрузка через Airflow:
![Incremental loading using airflow](./images/image-1.png)

Логи генератора с разной степенью детализации:
![INFO logs](./images/image-3.png)
![DEBUG logs](./images/image-4.png)

Полностью локальная инфраструктура со всем необходимым:
![Local infrastracture with all you've need](./images/image-5.png)


## 🚧 Выявленные, но пока не решённые проблемы
* Требуется 5-7 GB RAM для одновременной работы всей инфраструктуры на Win и Mac (docker desktop тяжёлый + работает много сервисов). [Рекомендуется увеличить виртуальную ОЗУ/файл подкачки](https://www.windowscentral.com/how-change-virtual-memory-size-windows-10).
* При каждом ```docker compose up``` инициализриуется airflow. Даги сохраняются, но ```Connections``` и ```Variables``` нужно вносить заново.


## 👷🏻 Об авторе
Разводов Алексей, Data engineer с 5+ годами опыта в индустрии. Стремлюсь передать своё понимание работы дата инженером и помочь тем, кто развивается на этом пути.

Если тебе помог и понравился этот репозиторий, поставь ему ⭐ и подпишись на соцсети.
* [Ментор](https://razvodov-mentorship-de.notion.site/About-me-and-mentorship_ru-06510bfd4bbd4dcba93c351df0ff4a0e)
* [Автор канала в tg о Data Engineering'e](https://t.me/rzv_de)
* [Автор публикаций в LinkedIn о Data Engineering'e](https://www.linkedin.com/in/razvodov-alexey/)
* [CV](https://docs.google.com/document/d/1tYi0s7yNsGl_Xts5CrHDegLvAtlHtz7jPSp074MfCyI/edit?usp=sharing)
* [Контакт для связи](https://t.me/razvodov_de_mentor)

<img src="images/photo.jpg" alt="Personal photo" width="300" style="display: block; margin: auto"/>
