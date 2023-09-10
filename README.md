# Улучшение представлений результатов в сервисе "Мой Голос"


## Данные

Json файлы с вопросом и ответами на него, для каждого ответа есть количество идентичных ответов других пользователей. <br> Также есть подобные файлы с разметкой о тональности ответа и информацией о его кластере.

## Задача

С помощью алгоритмов машинного обучения необходимо создать модели для объединения в группы ответов, схожих по смыслу с учетом тематики опроса. <br> Необходимо также визуализировать результат объединения и предложить альтернативные способы наглядного представления полученных результатов для пользователей сервиса.

## Используемые библиотеки

*Pandas* <br>
*Nltk* <br>
*Re* <br>
*Json* <br>
*Scikit-learn* <br>
*Spacy* <br>
*Numpy* <br>
*Torch* <br>
*transformers* <br>
*matplotlib* <br>

## OS итогового сервиса

Windows/linux

## Вывод
В рамках подготовки модели для сервиса была проведена следующая работа:
1.	Провел общий обзор данных, определена задача для обучения модели;
2.	Выбрал основной метод предобработки и векторизации текста с помощью spacy и Tf-Idf;
3.	Проверил работоспособность моделей кластеризации K-Means, DBSCAN и Agglomerative Clustering, за основу выбрана последняя;
4.	Модель протестировал на разных вариантах датасетов, что подтвердило ее эффективность для лейблинга кластеров на дальнейшей визуализации для пользователя
5.	Проверил предобработку текста с помощью LaBSE на выбранной модели, обосновал, почему не получится применить в текущей итерации сервиса.

Основная проблема заказчика на данном этапе решена – модель предоставляет возможность создания онлайн-опросника с автоматической визуализацией кластеризации ответов в реальном времени. С помощью топ 3 слов кластера получилось обозначить семантический смысл разделения пользовательских ответов на группы, а также удалось добиться высокой скорости предобработки текста и обучения, что позволит улучшить клиентский опыт с точки зрения ожидания результатов и их качества. <br> Основная проблема данной задачи состояла в том, что алгоритм должен быть максимально универсальным, так как опросы на сайте могут быть абсолютно любой направленности, а количество ответов очень сильно разнится от случая к случаю. Текущая версия модели позволяет с хорошей точностью разделить пользовательские ответы на группы с визуальным представлением на сайте. <br>В дальнейшем можно еще повысить качество модели, что было показано в пункте 5, однако на данном этапе у команды не хватает технических мощностей для реализации предобработки текста предобученной моделью, так как скорость обработки слишком низкая, что на данном этапе сильно ухудшит пользовательский опыт.
