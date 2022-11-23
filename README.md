# project_Auto_price
### The trying to predict how will be the car's cost.

### Помощник в определении стоимости лота на автоаукционе

В чем заключается выбор машины на японском аукционе для российского покупателя? По факту надо рассмотреть все машины, которые предлагают несколько аукционов для покупки на следующие несколько дней, выбрать те на которые хотите сделать ставку, и "угадать" правильную ставку. Количество ставок в день не более 5.  
Сложность в поиске компромисса. Если сделать большую ставку на машину с плохими характеристиками, то эта ставка сыграет сразу, но стоимость будет великовата для качества покупки, а если делать заниженные ставки, то можно играть очень долго, надеясь получить даром "коллекционный" экземпляр.  
Есть различные инструкции, как правильно выбирать, какие ставки делать, какие лоты смотреть в первую очередь. В оценке лота, всегда даются минимальная, максимальная и средняя стоимость продажи таких машин за какой-то период. И есть статистика продаж машин за последние 3 месяца. Все это помогает оценить машину очень приблизительно, но расчет самой ставки остается за покупателем, и чтобы начать более-меннее правильно оценивать, проходит, не меньше месяца.  
Мы имеем набор данных о продажах машин с их характеристиками за последние 3 месяца, с целевой переменной - стоимость продажи и также имеем несколько машин с их характеристиками, у которых надо определить эту стоимость. Задача контролируемого обучения - линейной регрессии. Если получится построить хорошую модель, то мы сможем достаточно быстро определять предполагаемую стоимость продажи такой машины и делать правильные ставки с первого дня на аукционе.  
  
  
**Что сейчас**  
Не все просто с интерпретацией. Результат все же неудовлетворительный!  
Как вариант можно попробовать перейти от задачи линейной регрессии к задаче классификации. К задаче классификации с 2-мя (неравномерными) классами. Скажем, не в полной мере я понимаю, как это может помочь. Есть ощущение, что так мы искусственно сами делаем часть работы (даже, наверно, большую часть работы) за машину и ей остается построить "линию", отсекающую классы, что например, на графике км/цена, кажется легко достижимым.  
Исходим из того, что у нас есть какой-то максимум бюджета в который нам надо уложиться. Предположим, что этот максимум - 400 тыс йен. Тогда, понимая, что мы хотим в этот бюджет взять нормальную машину, мы не расчитываем на поимку дешевого чуда, но небольшое чудо приветствуется, и не хотим рассматривать слишком дешевые ТС, така как там большой % некачественных машин. Тогда мы можем ограничить и нижнюю границу класса "1".  
Предположим что нижняя граница - 370 тыс йен.При этом тактика ставок будет максимально простой. Ставка будет всегда одна и та же - примерно, середина интервала.  
  
***Тогда класс "1" - машины состоимостью 370 - 420. Остальные - класс "0"***  
  
Так здесь можно и не только лог рег использовать, и деревья и KNN и вместе собрать pipeline.
