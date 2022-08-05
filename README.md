Привет! Это страничка Александра Богданова, IT-инженера, backend-программиста, тим-лида, IT-директора... и просто хорошего человека 🤗

Свою первую программу на BASIC-е, перепечатанную с книжки по программированию, я продал в 13 лет моему другу, и с тех под увлечение программированием меня не отпускает 😂

За 22 года мне удалось пройти путь от системного администратора небольшой локальной сети до руководителя направления интернет-продаж крупной производственной компании. За это время было реализовано множество разных проектов и накоплено множество скилов, которые помогают мне двигаться дальше и покорять российский IT. 

Настоящая моя страсть это технологии! Для меня высшее удовольствие находиться на острие современного IT, развивая себя и компании, где я работаю. 

## 🏗️ Реализованные проекты
<details>
<summary><strong>Переезд IT-инфраструктуры с Virtuozzo на Kubernetes на базе Яндекс.Облака</strong></summary>
<br />
<img src="assets/virtuozzo-to-yc.png" alt=""/>
<br />
🧐 <b>Кейс:</b> В процессе развития наших e-commerce сервисов мы заметили, что всё чаще отвлекаемся на проблемы, связанные с обеспечением мониторинга, доступности и надежности работы наших сервисов. То где-то кончатся ресурсы, то ляжет целый хост-сервер с кучей виртуалок "на борту". И хотя у нас были наработки по холодной и горячей замене, а также налажен процесс восстановления из бекапов, всё-таки хотелось тратить еще меньше времени на то, чтобы заниматься любимым делом - создавать любимые сервисы. Поэтому мы начали искать более гламурное решение. <br /><br />
❔ <b>Проблема:</b> Рассмотрев разные варианты (а среди них были: другое решение по виртуализации, приватное и публичное облако) мы остановились на варианте переезда в Яндекс.Облако. Причины, которые побудили нас это сделать:
<ul>
	<li>Серьезный крупный провайдер, который завтра не закроется</li>
	<li>Выполнение требования к лоализации данных</li>
	<li>По предварительным подсчетам стоимость выходила меньше (хотя здесь мы обманулись</li>
	<li>Встроенный по-умолчанию мониторинг и бекапы</li>
	<li>Решение проблем с доступностью благодаря наличию Managed Kubernetes</li>
	<li>Большое количество интересных сервисов, которые мы могли бы использовать в процессе развития наших сервисов</li>
</ul>
Выбрав решение, мы стали делать план переноса с текущей инфраструктуры в облако. По предварительным прикидкам выходило, что перенести предстояло порядка 130 сервисов, и переносить их в том виде, в каком они ранее работали (1 сервис - 1 виртуальная машина) не представляется возможным из-за очень высокой цены. <br /><br />
➡️ <b>Решение:</b> Было решено сразу начать оформлять каждый из сервисов в виде docker-образа и размещать сервисы в Kubernetes. Это, в свою очередь потребовало от нас изменить подход к разработке, внедрив полноценный CI/CD, но благо на базе платформы Kubernetes сделать это оказалось очень просто. <br /> Таким образом, в течение порядка 6 месяцев был произведен переезд внутренних корпоративных систем (WMS, CRM, CMS, PIM) в облако. <br /><br />
✅ <b>Результат:</b> Уже после переноса первых сервисов на новую платформу и настройку CI/CD удалось оценить, насколько стал удобен процесс разработки и обслуживания инфраструктуры. Релизы теперь делались гораздо быстрее (часы вместо дней), а контроль над состоянием инфраструктуры стал просто тотальным. К сожалению, я ушел из компании, когда процесс переезда еще только продолжался, поэтому полностью оценить весь спектр преимуществ от переезда мне не удалось. 
 <br /> <br />
<b>Используемый стек технологий:</b><br />
[![Kubernetes](https://img.shields.io/badge/IaaS-Kubernetes-yellow)](https://alexanderbogdanov.site)
[![Docker](https://img.shields.io/badge/Tools-Docker-black)](https://alexanderbogdanov.site)
[![Docker-compose](https://img.shields.io/badge/Tools-Docker%20compose-black)](https://alexanderbogdanov.site)
[![Helm](https://img.shields.io/badge/Tools-Helm-black)](https://alexanderbogdanov.site)
</details>

<details>
<summary><strong>Интеграция с системой Честный Знак</strong></summary>
<br />
<img src="assets/chesny_znak.jpg" alt=""/>
<br />
🧐 <b>Кейс:</b> Бизнес, в котором я работал, помимо всего прочего, продавал верхнюю одежду. С 1-го января 2021 года,  в соответствии с законодательством, такая одежда в обязательном порядке должна маркироваться специальными кодами формата DataMatrix, эмитировать которые поручено единому оператору - Центру Развития Перспективных Технологий (ЦРПТ), а сама система маркировки называется [Честный Знак](https://честныйзнак.рф). <br /><br />
❔ <b>Проблема:</b> Проблема заключалась в том, что данные коды являются аналогом акцизных марок для алкоголя, и учет должен производиться как на входе (при приёмке или возврате товара от покупателя), так и на выходе (при продаже или возврату поставщику). Учет должен быть стожайший, т.к., помимо штрафов, система накладывала множество ограничений на движение неучтенных кодов маркировки между организациями по линии продавец-поставщик или продавец-покупатель. Кроме этого, наличие кодов и необходимости дополнительного сканирования этого кода приёмщиками и продавцами на каждом из этапов движения товара вело к увеличению времени сборки заказов, что печалило руководство, а оно печалило нас...  Соответственно, учет этих кодов без использования какой-либо автоматизации являлся абсолютно нереалистичным. Ситуация усугублялась тем, что рынке не было приемлемых решений по маркировке товаров, т.к. сам рынок только создавался. <br /><br />
➡️ <b>Решение:</b>Изучив доступные на рынке решения, мы пришли к выводу, что они нам не подходят и стали думать над собственным решением. Изучив API множества подсистем системы Честный Знак (а подсистем было много - TRUE API, API ГИС МТ, СУЗ API и ряд других), они показались нам достаточно зрелыми и юзабельными (что не часто для API гос. компаний), и мы решили сделать собственное решение, автоматизирующее работу с данными кодами. Были разработаны:
<ul>
	<li>[PHP-библиотека](https://github.com/kilylabs/true-api-cli) для взаимодействием с API Честный Знак</li>
	<li>Интеграция между нашей складской WMS-системой и Честный Знак</li>
	<li>Закуплено оборудование для печати маркировки</li>
</ul><br /><br />
✅ <b>Результат:</b> Разработка заняла порядка 2-х месяцев, по итогам которой нам удалось практически полностью автоматизировать работу с кодами маркировки (за исключением участка приёмки и пересортицы). Более того, внедрение нашего решения позволило отслеживать историю движения каждого маркируемого товара, что дало маркетологам новую порцию интересных данных для анализа (например, почему одна и та же женская куртка продавалась и возвращалась 5 раз подряд на склад). Более того, в нашем решении нам удалось избавиться от необходимости двойного сканирования штрих кодов - самого штрих-кода изделия и DataMatrix кода Честного Знака. Таким образом, все операции по работе с макировкой производились прозрачно для комплектовщиков, и не приводили к увеличению сроков сборки заказов. 
<br /><br />
<b>Используемый стек технологий:</b><br />
[![PHP](https://img.shields.io/badge/Lang-PHP-blue)](https://alexanderbogdanov.site)
[![MySQL](https://img.shields.io/badge/DB-MySQL-orange)](https://alexanderbogdanov.site)
[![Yii](https://img.shields.io/badge/Framework-Yii-green)](https://alexanderbogdanov.site)

</details>

<details>
<summary><strong>Разработка и внедрение PIM (Product Information Management) системы</strong></summary>

Для более гибкого управления ассортиментом и ассортиментной политикой необходимо было вндрить систему класса Product Information Management. Проведя исследования существующих систем, ни одна из них не удовлетворяла необходимым критериям
(в основном, проблема была в стомости решения), и было решено разработать систему самостоятельно. В рамках создаиня этой системы было реализовано основные концепции PIM-системы, которые позволили централизовать хранение всей информации о продукции, поддерживать её в актуальном состоянии, а также ввести понятие "процент заполнения карточки товара".

Используемый стек технологий:
[![Angular](https://img.shields.io/badge/Framework-Angular-green)](https://alexanderbogdanov.site)
[![Laravel](https://img.shields.io/badge/Framework-Laravel-green)](https://alexanderbogdanov.site)
[![MySQL](https://img.shields.io/badge/DB-MySQL-orange)](https://alexanderbogdanov.site)
[![PHP](https://img.shields.io/badge/Lang-PHP-blue)](https://alexanderbogdanov.site)

</details>

<details>
<summary><strong>WMS</strong></summary>

TODO: найти время чтобы описать

</details>

<details>
<summary><strong>Интеграция управленческого учета на базе 1С</strong></summary>

TODO: найти время чтобы описать

</details>

<details>
<summary><strong>CRM</strong></summary>

TODO: найти время чтобы описать

</details>

<details>
<summary><strong>CMS-система</strong></summary>

TODO: найти время чтобы описать

</details>

<details>
<summary><strong>Интеграция аналитики ROISTAT</strong></summary>

TODO: найти время чтобы описать

</details>

## 💼 Скилы
[![C](https://img.shields.io/badge/Lang-C-blue)](https://alexanderbogdanov.site) [![GO](https://img.shields.io/badge/Lang-GO-blue)](https://alexanderbogdanov.site) [![JavaScript](https://img.shields.io/badge/Lang-JavaScript-blue)](https://alexanderbogdanov.site) [![Linux shell](https://img.shields.io/badge/Lang-Linix%20sehll-blue)](https://alexanderbogdanov.site) [![Python](https://img.shields.io/badge/Lang-Python-blue)](https://alexanderbogdanov.site) [![PHP](https://img.shields.io/badge/Lang-PHP-blue)](https://alexanderbogdanov.site) [![TypeScript](https://img.shields.io/badge/Lang-TypeScript-blue)](https://alexanderbogdanov.site) [![SQL](https://img.shields.io/badge/Lang-SQL-blue)](https://alexanderbogdanov.site)

[![MongoDB](https://img.shields.io/badge/DB-MongoDB-orange)](https://alexanderbogdanov.site) [![MySQL](https://img.shields.io/badge/DB-MySQL-orange)](https://alexanderbogdanov.site) [![Oracle](https://img.shields.io/badge/DB-Oracle-orange)](https://alexanderbogdanov.site) [![PostgreSQL](https://img.shields.io/badge/DB-PostgreSQL-orange)](https://alexanderbogdanov.site) [![Redis](https://img.shields.io/badge/DB-Redis-orange)](https://alexanderbogdanov.site)

[![Angular](https://img.shields.io/badge/Framework-Angular-green)](https://alexanderbogdanov.site) [![Flask](https://img.shields.io/badge/Framework-Flask-green)](https://alexanderbogdanov.site) [![Laravel](https://img.shields.io/badge/Framework-Laravel-green)](https://alexanderbogdanov.site) [![Ionic](https://img.shields.io/badge/Framework-Ionic-green)](https://alexanderbogdanov.site) [![Symfony](https://img.shields.io/badge/Framework-Symfony-green)](https://alexanderbogdanov.site) [![Yii](https://img.shields.io/badge/Framework-Yii-green)](https://alexanderbogdanov.site)

[![RabbitMQ](https://img.shields.io/badge/Message%20brokers-RabbitMQ-red)](https://alexanderbogdanov.site)

[![Ansible](https://img.shields.io/badge/IaaS-Ansible-yellow)](https://alexanderbogdanov.site) [![Kubernetes](https://img.shields.io/badge/IaaS-Kubernetes-yellow)](https://alexanderbogdanov.site) [![Terraform](https://img.shields.io/badge/IaaS-Terraform-yellow)](https://alexanderbogdanov.site)

[![Docker](https://img.shields.io/badge/Tools-Docker-black)](https://alexanderbogdanov.site) [![Docker-compose](https://img.shields.io/badge/Tools-Docker%20compose-black)](https://alexanderbogdanov.site) [![Composer](https://img.shields.io/badge/Tools-Composer-black)](https://alexanderbogdanov.site) [![Pip](https://img.shields.io/badge/Tools-Pip-black)](https://alexanderbogdanov.site) [![npm](https://img.shields.io/badge/Tools-Npm-black)](https://alexanderbogdanov.site) [![Helm](https://img.shields.io/badge/Tools-Helm-black)](https://alexanderbogdanov.site)

[![Yandex.Cloud](https://img.shields.io/badge/Cloud-Yandex.Cloud-white)](https://alexanderbogdanov.site) [![AWS](https://img.shields.io/badge/Cloud-AWS-white)](https://alexanderbogdanov.site)


