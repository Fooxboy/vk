---
layout: default
title: Метод Video.GetComments
permalink: video/getComments/
comments: true
---
# Метод Video.GetComments
Возвращает список комментариев к видеозаписи.

Страница документации ВКонтакте [video.getComments](https://vk.com/dev/video.getComments).
## Синтаксис
``` csharp
public ReadOnlyCollection<Comment> GetComments(VideoGetCommentsParams @params)
```

## Параметры
Класс **`VideoGetCommentsParams`** содержит следующие свойства:

+ **OwnerId** - Идентификатор пользователя или сообщества, которому принадлежит видеозапись. Обратите внимание, идентификатор сообщества в параметре owner_id необходимо указывать со знаком "-" — например, owner_id=-1 соответствует идентификатору сообщества ВКонтакте API (club1)  целое число, по умолчанию идентификатор текущего пользователя
+ **VideoId** - Идентификатор видеозаписи. положительное число, обязательный параметр
+ **NeedLikes** - 1 — будет возвращено дополнительное поле likes. По умолчанию поле likes не возвращается. флаг, может принимать значения 1 или 0
+ **StartCommentId** - Идентификатор комментария, начиная с которого нужно вернуть список (подробности см. ниже). положительное число, доступен начиная с версии 5.33
+ **Offset** - Смещение, необходимое для выборки определенного подмножества комментариев. По умолчанию — 0. целое число
+ **Count** - Количество комментариев, информацию о которых необходимо вернуть. положительное число, по умолчанию 20, максимальное значение 100
+ **Sort** - Порядок сортировки комментариев (asc — от старых к новым, desc — от новых к старым) строка
+ **Extended** - 1 — комментарии в ответе будут возвращены в виде пронумерованных объектов, дополнительно будут возвращены списки объектов profiles, groups. флаг, может принимать значения 1 или 0, доступен начиная с версии 5.0

## Результат
После успешного выполнения возвращает общее количество комментариев и массив объектов comment, каждый из которых содержит следующие поля: 

id — идентификатор комментария; 
from_id — идентификатор автора комментария; 
date — дата добавления комментария в формате unixtime; 
text — текст комментария; 
likes — информация об отметках «Мне нравится» текущего комментария (если был задан параметр need_likes), объект с полями: 

count — число пользователей, которым понравился комментарий, 
user_likes — наличие отметки «Мне нравится» от текущего пользователя 
(1 — есть, 0 — нет), 
can_like — информация о том, может ли текущий пользователь поставить отметку «Мне нравится» 
(1 — может, 0 — не может). 


Если был передан параметр start_comment_id, будет также возвращено поле real_offset – итоговое смещение данного подмножества комментариев (оно может быть отрицательным, если был указан отрицательный offset).

## Пример
``` csharp
// Пример кода
```

## Версия Вконтакте API v.5.44
Дата обновления: 26.01.2016 14:50:41