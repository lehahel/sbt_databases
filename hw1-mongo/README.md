## **Попов Алексей, Б05-927, отчет о домашнем задании по MongoDB**

1. MongoDB была развернута локально
2. Был загружен датасет с данными о различных заведениях с Yelp, ими была заполнена база данных (https://www.kaggle.com/yelp-dataset/yelp-dataset?select=yelp_academic_dataset_business.json)
3. Были выполнены запросы в базу данных
   - Получение всех записей: db.yelp_academic_dataset_business.find()
   - Выборка записей с более чем 1000 отзывами на Yelp: db.yelp_academic_dataset_business.find({"review_count": {"$gt": 1000}})
   - Получение названий заведений, подходящих для детей: db.yelp_academic_dataset_business.find({"attributes.GoodForKids": 'True'}, {"name": 1, "_id": 0})
   - Получение спортзалов:  db.yelp_academic_dataset_business.find({"categories": {"$regex": "\.*Gyms.\*"}})
   - Вставка нового заведения: db.yelp_academic_dataset_business.insertOne({"name": "New Pizzeria", "city": "Dolgoprudnij"})
   - Обновление информации о заведении: db.yelp_academic_dataset_business.updateOne({"name": "New Pizzeria"}, {"$set": {"stars": 5}})
4. Добавлены индексы на различные поля в базе, после этого скорость выполнения запросов (из прошлого пункта и не только) возросла в 3-10 раз в зависимости от запроса (для измерения использовался .explain("executionStats).executionStats)
5. Пример: запрос на получение спортзалов из п.3 выполнялся 240 мс, а после добавления индекса на поле "categories" - 26 мс
6. Видим, что индексы существенно ускоряют выполнение запросов в базу

### **Скриншоты**
![image](https://user-images.githubusercontent.com/56634370/157679861-2744acf6-64c5-4313-8761-fd02f506b21d.png)
![image](https://user-images.githubusercontent.com/56634370/157679940-c8796468-686b-4f34-aaf9-315361f08d5f.png)
![image](https://user-images.githubusercontent.com/56634370/157679989-f9122e36-dd16-4f8e-94db-6a26feec0a7c.png)
![image](https://user-images.githubusercontent.com/56634370/157680099-92163934-aa87-4609-91e1-7bbb51dbf2f9.png)
