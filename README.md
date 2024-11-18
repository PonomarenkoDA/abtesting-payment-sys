# Анализ результатов A/B - тестирования: система оплаты на сайте

## Описание: 
Команда образовательного проекта внедрила на сайт новую механику оплаты услуг – предполагается, что такая механика упростит процесс оплаты и поспособствует увеличению лояльности клиентов к проекту. Чтобы проверить эффективность новой механики оплаты услуг, был проведен АБ-тест. В группе B (тестовой) оказались пользователи с новой системой оплаты услуг, в группе A (контрольной) пользователи со старой версией системы, где не используется новая механика. <br/>

**Сделать аналитическое заключение с ответом на вопрос, стоит ли включать систему оплаты услуг с новой механикой на всех пользователей.**<br/>

**Для анализа использовался следующий стек технологий**: <br/>

![Python](https://img.shields.io/badge/-Python-0b0038?style=for-the-badge&logo=python&logoColor=3c78a9)
![Pandas](https://img.shields.io/badge/pandas-0b0038?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-0b0038?style=for-the-badge&logo=numpy&logoColor=4c74cc)
![Scipy](https://img.shields.io/badge/-Scipy-0b0038?style=for-the-badge&logo=scipy&logoColor=white)
![Statsmodels](https://img.shields.io/badge/pingouin-0b0038?style=for-the-badge&logo=statsmodel&logoColor=white)
![Seaborn](https://img.shields.io/badge/seaborn-0b0038?style=for-the-badge&logo=seaborn&logoColor=white)
![Matplotlib](https://img.shields.io/badge/matplotlib-0b0038?style=for-the-badge&logo=matplotlib&logoColor=white)
![Requests](https://img.shields.io/badge/requests-0b0038?style=for-the-badge&logo=requests&logoColor=white)

## Выполненные задачи:

1. Автоматизирован процесс загрузки исходных датасетов с использованием API Яндекс.Диска.

2. Проведен  разведочный анализ данных (EDA-анализ) в ходе которого для каждого датафрейма в данных определены аномалии, количество уникальных значений, пропусков, дубликатов и т.д. 

3. Выбраны и рассчитаны целевые метрики, косвенно характеризующие эффективность системы оплаты на сайте: конверсия из посещений сайта в оплату услуги (CR), средний доход с платящего пользователя (ARPPU).

4. Автоматизирован процесс пересчета и визуализации целевых метрик, отражающих результаты АБ-тестирования, при обновлении данных в исходном файле df_groups_add.csv.

    ![metrics](https://github.com/PonomarenkoDA/images/blob/main/business_metrics_$.png?raw=true)

5. Проведен расчет размера выборок в группах (control/test) и построены гистограммы распределений данных для каждой метрики.

6. Использованы методы статистического анализа для проверки гомогенности дисперсий (тест Левена) и нормальности распределения данных в группах (тест Д'Агостино-Пирсона, Q-Q plot для визуальной оценки).

7. Выбраны и использованы методы статистического анализа для оценки значимости изменений в метриках:
   (критерий Хи-квадрат Пирсона, Bootstrap)
   
    <!-- ![avg_revenue](https://github.com/PonomarenkoDA/images/blob/main/avg_paying_rev.png?raw=true) -->
        
    <!-- ![bootstrap](https://github.com/PonomarenkoDA/images/blob/main/bootstrap.png?raw=true) -->
8. Проведена оценка результатов А/B-теста и сделано аналитическое заключение.

9. Подключение к базе данных образовательного проекта (Python + SQL).
10. Реализован оптимальный SQL-скрипт для подсчета наиболее активных пользователей проекта за последний месяц (наиболее активными пользователеми считаем пользователей, которые решили более 20 заданий на платформе).
11. Реализован SQL-скрипт для расчета актуальных метрик одним запросом: ARPU, ARPAU, CR в покупку, СR активного пользователя в покупку, CR пользователя из активности по математике в покупку курса по математике.

## Полученный результат:
При использовании новой механики оплаты услуг не обнаружено существенное изменение конверсии из посещений сайта в оплату, однако статистически значимо повышается средний доход бизнеса с платящего пользователя.
**Следовательно, система оплаты с новой механикой считается эффективной и рекомендуется включать ее для всех пользователей.**

<!-- ## Исходные данные: 

1. **ab_users_data** - таблица c информацией о заказах:

    `user_id` - позаказный идентификатор пользователя; <br/>
    `order_id` - уникальный идентификатор заказа (номер чека);<br/>
    `action` - действие пользователя: create_order или cancel_order;<br/>
    `time` - время совершения действия;<br/> 
    `date` - дата совершения действия;<br/> 
    `group` - принадлежность пользователя к группе при АБ-тесте.

2. **ab_orders** - таблица с информацией о составе заказов:

    `order_id` - уникальный идентификатор заказа (номер чека);<br/>
    `creation_time` - время создания заказа;<br/> 
    `product_ids` - состав каждого заказа (в виде списка id товаров).<br/> 

3. **ab_products** - таблица с информацией товарных позициях:

    `product_id` - уникальный идентификатор товара;<br/>
    `name` - название товара;<br/> 
    `price` - цена товара.<br/>  -->

<!-- 
- Информация о заказах `df_orders`
- Информация о клиентах `df_customers`
- Информация о товарах в составе заказа `df_order_items` -->
<!-- <style>
ul {
    list-style-type: none; /* Убираем маркеры у ненумерованных списков */
    padding: 0; /* Убираем отступы */
}
</style>

<ul>

<details> 
    <summary>Информация о заказах `df_orders` <u>(см. подробнее)</u></summary>
    <p>

`order_id` - уникальный идентификатор заказа (номер чека)  
`customer_id` - позаказный идентификатор пользователя  
`order_status` - статус заказа  
`order_purchase_timestamp` - время создания заказа  
`order_approved_at` - время подтверждения оплаты заказа  
`order_delivered_carrier_date` - время передачи заказа в логистическую службу  
`order_delivered_customer_date` - время доставки заказа  
`order_estimated_delivery_date` - обещанная дата доставки  
</p>
</details>
</ul>

<ul>

<details> 
    <summary>Информация о заказах `df_customers` (см. подробнее)</summary>
    <p>

`customer_id` - позаказный идентификатор пользователя  
`customer_unique_id` - уникальный идентификатор пользователя (аналог номера паспорта)  
`customer_zip_code_prefix` - почтовый индекс пользователя  
`customer_city` - город доставки пользователя  
`customer_state` - штат доставки пользователя
</p>
</details>
</ul>

<ul>

<details> 
    <summary>Информация о заказах `df_order_items` (см. подробнее)</summary>
    <p>

`order_id` - уникальный идентификатор заказа (номер чека)  
`order_item_id` - идентификатор товара внутри одного заказа  
`product_id` - ид товара (аналог штрихкода)  
`seller_id` - ид производителя товара  
`shipping_limit_date` - максимальная дата доставки продавцом для передачи заказа партнеру по логистике  
`price` - цена за единицу товара  
`freight_value` - вес товара

</p>
</details>
</ul> -->
