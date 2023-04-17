# Домашнее задание к занятию 10.3 «Pacemaker» - Куприянов Владимир


### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c Шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и вашу фамилию и имя
   - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
   - для корректного добавления скриншотов воспользуйтесь инструкцией ["Как вставить скриншот в шаблон с решением"](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
   - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.

Желаем успехов в выполнении домашнего задания!

---

### Задание 1

Опишите основные функции и назначение Pacemaker.

*Приведите ответ в свободной форме.*

Назначение Pacemaker, как менеджера ресурсов кластера - обеспечивать достижение максимальной доступности ресурсов (при этом ресурсом кластера может быть все, что можно заскриптовать), обнаружение сбоев, восстановление работоспособности (узлов и сервисов) и поддержка любого количества узлов в кластере.

Основные функции Pacemaker:
- Обнаружение и восстановление неисправностей на уровне сервисов и узлов кластера.
- Поддержка STONITH (Shoot-The-Other-Node-In-The-Head) - средство для вывода "умершего" узла из кластера (в том числе проблему "Split-Brain", когда связь между узлами теряется, но оба они живы, но каждый из них думает, что другой умер и пытается забрать все ресурсы себе)
- Поддержка ресурсозависимых и кворумных кластеров (Pacemaker поддерживает практически любую избыточную конфигурацию).
- Поддержка расширенных типов ресурсов, таких как клоны и дополнительные состояния.
- Pacemaker не зависит от подсистемы хранения и типов ресурсов.
- Поддержка авторепликации конфигурации на все узлы кластера.
- Поддержка возможности задать порядок запуска и остановки приложений и их совместимости на одном узле.
---

### Задание 2

Опишите основные функции и назначение Corosync.

*Приведите ответ в свободной форме.*

Corosync - программный продукт, позволяющий реализовать кластер серверов, а основное его назначение - знать и передавать состояние всех участников кластера.

Основные функции и назначение Corosync:
- Corosync отслеживает и передает состояние всех нод в кластере.
- Предоставляет доступ к общей БД с конфигурацией и статистикой и отправлять уведомления об изменениях в БД.
- Отправляет идентичные сообщения процессам на всех нодах.
- Позволяет отслеживать статус приложений
- Единый кластерный шелл (crm), унифицированный, скриптующийся.
- Оповещает приложения о смене активной ноды в кластере.

---

### Задание 3

Соберите модель, состоящую из двух виртуальных машин. Установите Pacemaker, Corosync, Pcs. Настройте HA кластер.

*Пришлите скриншот рабочей конфигурации и состояния сервиса для каждого нода.*

Нода 1

![image](https://user-images.githubusercontent.com/124167007/232593830-8050d34e-e191-45f1-917c-616c000f018c.png)

![image](https://user-images.githubusercontent.com/124167007/232593876-26d8e12b-dfb5-41c3-856b-2e2d51914c55.png)

![image](https://user-images.githubusercontent.com/124167007/232594360-2a94341c-562a-414a-8028-d12936900fd8.png)


Нода 2

![image](https://user-images.githubusercontent.com/124167007/232593995-548278a3-0dcf-48ad-801f-c80c5c50845c.png)

![image](https://user-images.githubusercontent.com/124167007/232594029-6401b76e-1d3f-4444-b291-9e1a21b61355.png)

![image](https://user-images.githubusercontent.com/124167007/232594439-d828ca46-9ecb-4930-a15c-2884444ec1cb.png)

![image](https://user-images.githubusercontent.com/124167007/232594082-339671ac-d329-462e-942f-8a6112587d98.png)

![image](https://user-images.githubusercontent.com/124167007/232594107-2a813173-e81f-4db6-bef4-ed678245139c.png)

![image](https://user-images.githubusercontent.com/124167007/232594225-1dc4d0f6-8af9-4496-930a-ff0e5efaf11a.png)

![image](https://user-images.githubusercontent.com/124167007/232594273-60423bea-5382-4d1a-9ba6-c131daf6a433.png)

---

### Задания со звёздочкой*
Эти задания дополнительные. Выполнять их не обязательно. Это не повлияет на зачёт. Вы можете их выполнить, если хотите глубже разобраться в материале.
 
---

### Задание 4

Установите и настройте DRBD-сервис для настроенного кластера.

*Пришлите скриншот рабочей конфигурации и состояние сервиса для каждого нода.*

