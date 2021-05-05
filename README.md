## SpellChecker на основе записей википедии для русского языка  

### Существующие недостатки:  

1) Низкая скорость первичного формирования словаря  

2) Требование к внешней памяти: должно быть не менее 20 гигабайт свободной внешней памяти на устройстве, на котором расположен скрипт.
Разархивирванные тексты википедии весят именно столько.  
 
Возможное решение перечисленных выше проблем: загрузка не текстов самой википедии, а готового словаря в виде файла, обработанного ранее. 

3) Наличие ряда ошибок в сформированном словаре. А именно:  

отсутсвие неспецифичных для википедии слов: решается расширением исходного набора текстов или полной его заменой  

встречаемые сокращения: возможно формирование словаря общепринятых сокращений, дабы отфильтровывать
их на этапе формирования целевого словаря  

ошибки в самой википедии: решение - лишь замена набора текстов  

наличие в википедии слов на других языках, написанных кириллицей: как правило, таковые встречаются в разделе "примечания". 
На этапе парсинга возможна обработка таких случаев. Однако тогда может пострадать разнообразие формируемого словаря (в этом разделе также
 встречается множество слов русского языка)     


### Скорость работы  
Сам по себе спеллчекер работает быстро (O(1), так как проверка на вхождение осуществляется через хеш-функцию).
Медленно работает загрузка всех текстов и формирование словаря (порядка 1.5 часов), или, если словарь был сформирован ранее, относительно медленно работает загрузка готовых слов (несколько секунд).    


### Подробнее про встречаемые ошибки  

1) Отсутствие ряда неспецифичных для википедии слов.  
Например, слова "коробчонка" и "пятипалость" отсутствуют в сформированном словаре.  

2) В качестве слов попадаются сокращения.  
К примеру, следующие слова попали в словарь: "комм", "прим".  

3) В википедии встречаются ошибки.  
Например, слова "рассизм", "еденица" и "стотоянию" попали в словарь.  

4) Слова на других языках, написанных кириллицей.  
Пример: слово "йнялняю" попало в словарь  
