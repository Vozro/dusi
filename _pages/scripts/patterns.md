---
layout: default
title: Скрипты - Шаблоны фраз
permalink: /scripts/patterns/
---

Один из типов событий в скриптах - Фраза.
С помощью нее вы можете запускать скрипт, сказав какую-то специальную команду.

Шаблоны необходимы, когда скрипт должен реагировать не просто на свое название, а на гораздо более свободные фразы.

Еще шаблоны нужны, если мы хотим получить из нашей речи некоторые данные, которые потом нужно куда-то передать или как-то обработать в скрипте.

_Шаблон — это по сути форма той команды, которую мы будем давать ассистенту._

## Синтаксис шаблонов

Чтобы писать шаблоны, нужно изучить их синтаксис. Он был разработан специально для работы с распознаваемой речью.

Вот пример простого шаблона:

`* добр* утр* *`

Под него подойдут любые фразы, которые начинаются с любых слов (первая звездочка). Затем должно идти слово, начинающееся с добр. Затем должно идти слово, начинающееся с утр. И заканчиваться наша фраза может опять же любыми словами (последняя звездочка).

Как видите, синтаксис интуитивно понятен. Но конечно же, он имеет гораздо более гибкие элементы, которые описаны ниже.

### Звездочки

Самый частый элемент. Звездочка обозначает любое количество любых символов, в том числе ни одного.
Звездочку можно либо окружать пробелами — тогда она означает слово или несколько слов, либо ставить вплотную к слову в начале или в конце. 
Тогда она означает, что слово может начинаться и заканчиваться любыми символами.

**Ставить звездочку в середину слова нельзя**

### Альтернативы

Позволяют описать альтернативные слова и словосочетания, которые могут идти в определенной позиции. Например — `(утро|день|вечер|ночь)`

Уровень вложенности — любой.

### Опции

Позволяют указать, что какие-то слова и словосочетания необязательны во фразы, но могут присутствовать. Например — `[привет|пока]`

### Перестановки

Обозначает, что слова в скобках могут идти в любом порядке. Например — `{дуся как дела}`

### Ссылки

Позволяют указать, что в данной позиции должно идти что-то, что подходит под указанный шаблон. Например — скажи фразу `$Text`
Здесь `$Text` — это ссылка на шаблон, который подходит под любой текст.

Еще пример — `$Number плюс $Number` — обозначает, что во фразе должно быть два числа, а между ними слово "плюс".

Ниже вы найдете список шаблонов, которыми вы можете пользоваться.

## Стандартные шаблоны

$Text — обычный текст (одно или несколько слов, или пустой текст)

$Number — число

$Date — дата (абсолютная и относительная)

$Time — время (абсолютное и относительное)

$Contact — имя контакта в любом падеже (должно соответствовать полному имени контакта)

$Address — адрес (произвольная улица, либо один из заранее сохраненных адресов типа «дом», «работа» и так далее)

$Lang - название языка

Когда во фразе попадается тот или иной шалон, то при срабатывании события Фраза генерируются [специальные переменне](/scripts/vars/) для каждого из них.

## Синонимы

Позволяют использовать в одном шаблоне сразу несколько шаблонов с одинаковым именем, чтобы потом к ним можно было обратиться по синониму.
Например — `$N1::Number плюс $N2::Number`

Здесь `$N1` и `$N2` — это синонимы. Иначе нельзя было бы различить по имени два разных числа во фразе.