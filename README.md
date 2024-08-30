# Прогнозирование удоя для экофермы

**Цель и задачи:** разработать модель МО для владелеца молочного хозяйства «Вольный луг». Первая модель будет прогназировать возможный удой коровы, вторая - рассчитывать вероятность получить вкусное молоко от коровы.

# Вывод

По результатам прогнозирования ключевых метрик, фермеру рекомендовано приобрести 2 коровы из первоначальных данных с минимальным риском для своего хозяйства.Это обусловлено тем, что:
1. Риск потерь минимален благодаря успешной модели предсказания удоя, которая имеет высокий показатель прогноза (82%) и небольшую среднюю ошибку (146 кг). Для улучшения предсказания удоя нужно добавить новые признаки, например условия содержания коров, частота дояения коров и т.д.
2. Исходя из ТЗ, выборка коров осуществлялась только среди тех, у которых молоко является вкусным. Было исключены ошибки 1 рода, но сильно упала точность модели до 46%. Для более точного предсказания лучше чтобы ошибка допускалась, тогда модель будет более точнее давать прогноз.

В проекте использовались 2 модели:
1. Линейная с метриками  MAE, MSE, MRSE и коэффицент детерминации R2. Лучше всего получислось интерпритовровать модель с первым и последним показателем. C помощью MAE мы сравниваем качество модели по мере настройки обучения, а R2 нужен для сравнения двух регриссионных моделей. При корелляционном анализе выявили, что удой не имеет линейную связь с такими признаками, как :ЭКЕ и СПО. Признак ЭКЕ была возведена в квадрат, а СПО - сделали категориальным признаком. После преобразовавания качество модели значительно улучшилось. Для последней модели добавили признак имя отца, не сказать что точность модели сильно увеличилась (а точнее никак не поменялась), но ошибок стало меньше. Было решено взять последнюю модель для прогнозирования удоя для cow_buy.
2. Логистическая регрессия с метриками Accuracy, Precision, Recall. Взяли метрики Accuracy, Precision, исходя из ТЗ заказчика. Accuracy покзывает доля правильных ответов, а Precision долю объектов, названных классификатором положительными и при этом действительно являющимися положительными. В ходе изучения модели и постановки первичной задачи, было решено изменить порого классификации, что привело исключение ошибок FP, но, как было выше сказанно, уменьшилосб точность модели.
