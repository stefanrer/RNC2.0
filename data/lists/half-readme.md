# Списки для выделения дополнительных лемм в композитах  

Предполагается дописывать в xml-представлении дополнительные разборы типа  
`<ana lex="пол" gr="COM"></ana>`  
для регулярных композитов по следующим правилам (определяются по лемме слова):
1. ПОЛ (полголовы) - `<ana lex="пол" gr="COM"></ana>`    
Часть речи: NOUN или PROPN или ADJ или ANUM или PRON (в нотации НКРЯ: S, A, ANUM, SPRO)     
шаблон: `пол*а, пол*я, пол*ы, пол*и, пол*го, пол*ой, пол*ых`  
И начинается не с: `поли*, полу*, полно*`  
И не содержит слов из списка в файле half.txt  
`+` добавить полноги, полночи, полнормы  

Примечание: разбор второй части слова пока не дописывается, в todo

2. НЕ (небритый) - `<ana lex="не" gr="PART"></ana><ana lex="брить" gr="V"></ana>`    
Часть речи: VERB или AUX (в нотации НКРЯ: V)   
И грамматическая помета `VerbForm=Part или VerbForm=Conv`
шаблон: `не*`   
И не начинается с: `недо*`  

3. ПОЛУ (полуснятый) -  `<ana lex="не" gr="PART"></ana>`  
Часть речи: VERB (в нотации НКРЯ: V)    
И грамматическая помета `VerbForm=Part или VerbForm=Conv`
шаблон: `полу*`   
И не начинается с: `недо*`  
И не содержит слов из списка в файле half.txt  

Примечание к 2-3. Если лемма глагола начинается с дефиса, его нужно удалить (и вообще полезно удалить все дефисы из начала строки атрибута lex)  

4. Если лемма содержит внутри знак +, то ее лемма разбивается на две части так:  
Было: не+быть  
Стало `ana lex="быть"...></ana><ana lex = "не"></ana>`  
Сама лемма с плюсом не записывается  
