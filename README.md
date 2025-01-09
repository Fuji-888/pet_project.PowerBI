#  Дашборд по продажам в PowerBI

#### Выполнил его в процессе изучения курса "Microsoft Power BI для бизнес-аналитики". 

  Выбрал я этот курс, потому что мне нужно было точечно с нуля разобраться, как работать с инструментом для BI. Остановился на PowerBI, потому что провел небольшой ресерч по вакансиям, статьям на хабре, видео и понял, что его используют чаще (на момент ресерча). Далее нашел несколько курсов и выбрал из них более подробный и с большим кол-вом практики. 
  
   В этом курсе оказался большой упор на различные DAX формулы.
   
   Но стиль визуализации мне не понравился, но я решил его не менять, так как я изучал основы работы с PowerBI. 
Визуализацию, которая мне нравится, я сделал в [СВОЕМ ПЕТ ПРОЕКТЕ](https://github.com/Fuji-888/pet_project.SQL_PowerBI) после этого курса.

![Иллюстрация к проекту](https://github.com/Fuji-888/pet_project.PowerBI/blob/main/pbi_cycles1.png)
![Иллюстрация к проекту](https://github.com/Fuji-888/pet_project.PowerBI/blob/main/pbi_cycles2.png)
![Иллюстрация к проекту](https://github.com/Fuji-888/pet_project.PowerBI/blob/main/pbi_cycles3.png)

## В этом курсе я научился:
* подключаться и преобразовывать данные с помощью Power Query;
* строить модель данных;
* использовать вычисляемые столбцы и меры с применением языка DAX;
* использовать функции даты и времени, логические и условным выражения, текстовые, CALCULATE, ALL, FILTER;
* создавать интерактивный дашборд;
* изучил принципы фильтрации, взаимодействие между графиками

## Примеры DAX формул, которые я изучил в этом проекте:

+ Месяц короткий = UPPER(LEFT(AW_Calendar_Lookup[Название месяца],3))
+ Выходной = IF(AW_Calendar_Lookup[День недели]=6 || AW_Calendar_Lookup[День недели]=7,"Да","Нет")
+ Возраст = DATEDIFF(AW_Customers_Lookup[BirthDate],NOW(),YEAR)
+ Customer Priority = IF(AW_Customers_Lookup[Возраст]>50 && AW_Customers_Lookup[AnnualIncome]>100000,"Приоритет","Стандарт")
+ Avg Price = AVERAGE(AW_Products_Lookup[ProductPrice])
+ Overall Avg Price = CALCULATE([Avg Price],all(AW_Products_Lookup))
+ Prev Month Returns = CALCULATE([Return Cases],DATEADD(AW_Calendar_Lookup[Date],-1,MONTH))
+ Return Rate = DIVIDE([Total Returns],[Quantity Sold], "нет продаж")
+ Return Cases = COUNTA(AW_Returns[ReturnQuantity])
+ Доход = SUMX(AW_Sales,AW_Sales[OrderQuantity] * RELATED(AW_Products_Lookup[ProductPrice]))

