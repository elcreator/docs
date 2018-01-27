##Templates

По умоланию считается, что в параметрах шаблона передано имя чанка. Но если имя чанка начинается с символа @, то происходит сверка начального слова в имени шаблона с заранее зарезервироваными правилами загрузки шаблонов. Все последующие слова используется в качестве параметра к выбранному правилу.

__@FILE__
Загрузка шаблона из html файла расположенного в папке или подпапках assets/templates/

__@CHUNK__
Обычная загрузка шаблона из чанка

__@TPL, @CODE__
Значение параметра используется в роли inline шаблона

__@DOCUMENT, @DOC__
Шаблон берется из content поля указанного документа

__@PLH, @PLACEHOLDER__
Шаблон загружается из глобального плейсхолдера MODX

__@CFG, @CONFIG, @OPTIONS__
Шаблон берется из глобальных настроек текущей установки MODX Evolution

Стоит заметить, что даже если начальный символ был @ и после обработки всех правил шаблон все равно оказался пустым, то происходит попытка обнаружить чанк по полному имени шаблона

##Плейсхолдеры

Плейсхолдеры в DocLister:

* плейсхолдер таблицы, имя такого плейсхолдера совпадает с названием колонки в таблице;
* виртуальный плейсхолдер, который стал доступен после запуска экстендера или каких-то вычислений внутри контроллера;
* глобальный плейсхолдер, который доступен из вне шаблонов передаваемых в сниппет (как правило имеет префикс dl и может быть переопределен при помощи параметров sysKey или id).

> Экстендер в DocLister - это вспомогательный класс для каких-либо обработок, не имеет ничего общего с экстендерами Ditto.

###Плейсхолдеры таблицы

Если указан контроллер site_content или любой другой его расширяющий, то по умолчанию используется таблица site_content. В случае с контроллером onetable имя таблицы определяется параметром table. Таким образом, получить полный список плейсхолдеров можно открыв таблицу mysql, например, через phpmyadmin и подсмотрев какие в этой таблице имеются поля.

###Виртуальный плейсхолдер

####Плейсхолдеры устанавливаемые экстендером paginate

__[+параметр_id.pages+]__
Пагинация

__[+параметр_id.totalPages+]__
Общее число страниц

__[+параметр_id.isstop+]__
1 если текущая страница — последная

__[+параметр_idisstart+]__
1 если текущая страница — первая

####Плейсхолдеры устанавливаемые экстендером jotcount

Экстендер загружается, если при вызове сниппета задан параметр __&jotcount__.

__[+jotcount+]__
Число комментариев из сниппета JOT

####Плейсхолдеры устанавливаемые экстендером tv

__[+tv.имяТВпараметра+]__
Значение ТВ параметра

По умолчанию ко всем ТВ параметрам добавляется префикс tv, но от него можно избавиться или переопределить параметром tvPrefix.

####Плейсхолдеры устанавливаемые экстендером e

Экстендер загружается, если при вызове сниппета задан параметр __&е=`имена полей через запятую`__

__[+e.имяПоля+]__
Экранированное значение поля.

####Плейсхолдеры устанавливаемые экстендером summary

__[+summary+]__
Аннотация к странице

####Плейсхолдеры устанавливаемые экстендером user

Экстендер необходимо загрузить вручную, указав его имя в параметре &extender. Также должны быть заданы параметры:
* usertype - возможные значения: manager, mgr, web. Определяет из каких таблиц брать данные пользователей;
* userFields - названия колонок через запятую, в которых указан id пользователя, например createdby, publishedby.

__[+user.id.НазваниеКолонки+]__
ID пользователя

__[+user.username.НазваниеКолонки+]__
Логин пользователя

__[+user.fullname.НазваниеКолонки+]__
Полное имя пользователя

__[+user.role.НазваниеКолонки+]__
ID роли пользователя

__[+user.email.НазваниеКолонки+]__
e-mail

__[+user.phone.НазваниеКолонки+]__
Телефон

__[+user.mobilephone.НазваниеКолонки+]__
Мобильный телефон

__[+user.blocked.НазваниеКолонки+]__
Статус блокировки

__[+user.blockeduntil.НазваниеКолонки+]__
До какого UNIX-времени пользователь будет заблокирован

__[+user.blockedafter.НазваниеКолонки+]__
После какого UNIX-времени пользователь будет заблокирован

__[+user.logincount.НазваниеКолонки+]__
Общее число авторизаций

__[+user.lastlogin.НазваниеКолонки+]__
UNIX-время последней авторизации

__[+user.thislogin.НазваниеКолонки+]__
UNIX-время текущей авторизации

__[+user.failedlogincount.НазваниеКолонки+]__
Число неудачных попыток авторизоваться

__[+user.lastlogin.НазваниеКолонки+]__
UNIX-время последней авторизации

__[+user.dob.НазваниеКолонки+]__
Дата рождения

__[+user.gender.НазваниеКолонки+]__
Пол

__[+user.country.НазваниеКолонки+]__
Страна

__[+user.state.НазваниеКолонки+]__
Регион

__[+user.zip.НазваниеКолонки+]__
Почтовый индекс

__[+user.fax.НазваниеКолонки+]__
Факс

__[+user.photo.НазваниеКолонки+]__
Фотография

__[+user.comment.НазваниеКолонки+]__

####Плейсхолдеры устанавливаемые в контроллерах site_content

__[+title+]__
Название документа для списков. Если menutitle пуст, то используется pagetitle

__[+iteration+]__, __[+ЗначениеПараметраsysKey.full_iteration+]__
Порядковый номер элемента в списке; порядковый номер в списке с учетом пагинации.

**Примечание:** для контроллера **site_content** и для контроллера **shopkeeper** плейсхолдер [+iteration+] выглядит как указано выше - [+iteration+] без префикса, а для контроллера **onetable** - как [+ЗначениеПараметраsysKey.iteration+] с префиксом. Префикс ЗначениеПараметраsysKey по умолчанию равен dl, то есть для **onetable** этот плейсхолдер по умолчанию - [+dl.iteration+].

__[+url+]__
Ссылка на документ

__[+date+]__
дата публикации документа сформированая по правилам указаным в параметре dateFormat (по умолчанию %d.%b.%y %H:%M). Помимо этого учитывается server_offset_time в настройках движка.

__[+ЗначениеПараметраsysKey.active+]__
Флаг определяющий, что обрабатываемый документ совпадает и документ на котором был вызван сниппет это одно и тоже (1 - если правда, 0 если нет)

__[+ЗначениеПараметраsysKey.class+]__
Классы которые могут быть автоматически присвоены документу (first, last, current, odd, even)

__[+ЗначениеПараметраsysKey.wrap+]__
HTML код списка подготовленный для вывода пользователю (используется только для шаблона ownerTPL)

##Параметры для установки плейсхолдеров

###sysKey

Префикс для системных плейсхолдеров.

Возможные значения - любая строка. На выходе получается плейсхолдер с именем [+sysKey.placeholder+], где sysKey это значение данного параметра

Значение по умолчанию - dl

###id

Префикс для локальных плейсхолдеров.

Возможные значения - любая строка. Если id указано, то на выходе получается [+id.placeholder+]. Где id это и есть переданое значение. В случае если id не задано, то перед именем плейсхолдера точка не ставится.

Значение по умолчанию - пусто.

##Параметры вывода в шаблоны

###ownerTPL

Шаблон в который оборачивается список результатов. Если подходящих результатов не обнаружено, то по умолчанию результат с шаблоном noneTPL тоже оборачивается в этот шаблон. За подробностями обращайтесь к описанию параметра noneWrapOuter.

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию - пусто.

####Пример:
```
&ownerTPL=`@CODE:
<ul class="pages-list">
    [+dl.wrap+]
</ul>
`
```

###tpl

Шаблон. 

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister. Значение параметра может быть изменено из prepare-сниппета c помощью свойства $_DocLister->renderTPL.

Значение по умолчанию - определяется в контроллере.

####Пример:
```
&tpl=`@CODE:
<li>
    <img src="[+tv.image+]" alt="[+e.pagetitle+]">
    <a href="[+url+]">[+title+] ([+id+])</a>
</li>
`
```

###tplId1, tplId2, ..., tplIdN

Шаблон для оформления документа под номером 1, 2 и т.д., где номер - это номер итерации начиная с 1.

Значение по умолчанию берется из значения параметра tpl.

**Примечание:** Обратите внимание, Id в названиях шаблонов не должно вводить вас в заблуждение, на самом деле номер - это не Id документа, а его номер по порядку в выводе (номер итерации).

###tplOdd, tplEven

Шаблон для оформления четного/нечетного документа.

Значение по умолчанию берется из значения параметра tpl.

###tplFirst

Шаблон для оформления первого документа в списке. Синоним параметра tplId1, но имеет больший приоритет.

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister. Если не задано, то совпадает с шаблоном tpl.

Значение по умолчанию - пусто.

###tplLast

Шаблон для оформления последнего документа в списке.

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister. Если не задано, то совпадает с шаблоном tpl.

Значение по умолчанию - пусто.

###tplСurrent

Шаблон для оформления текущего документа в списке документов. 

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister. Если не задано, то совпадает с шаблоном tpl.

Значение по умолчанию - пусто.

###noneTPL

Шаблон с уведомлением о том, что по заданным критериям ничего не обнаружено.

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию - пусто.

###noneWrapOuter

Оборачивать ли ответ noneTPL в шаблон ownerTPL. Параметр актуален только в том случае, если нет документов для построения списка и задан ownerTPL.

Возможные значения - 1 или 0.

Значение по умолчанию - 1.

##Пагинация

###paginate

Вывод данных с пагинацией. Смотрите плейсхолдеры устанавливаемые экстендером paginate.

Возможные значения:

* offset - пагинация в стиле Ditto;
* pages - пагинация с прострелами.

Значение по умолчанию - pages.

###TplFirstP

Шаблон для вставки ссылки "первая страница".

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию: пусто.

###TplLastP

Шаблон для вставки ссылки "последняя страница".

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию: пусто.

###TplNextP

Шаблон для вставки ссылки "следующая страница".
Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию:
```
@CODE: <a href="[+link+]">' . $this->DocLister->getMsg('paginate.next', 'Next') . ' ></a>
```

Плейсхолдеров для подстановки данных из языкового пакета пока нет.

###TplPrevP

Шаблон для вставки ссылки "предыдущая страница".

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию:
```
@CODE: <a href="[+link+]">< ' . $this->DocLister->getMsg('paginate.prev', 'Prev') . '</a>
```

Плейсхолдеров для подстановки данных из языкового пакета пока нет.

###TplPage

Шаблон для вставки номера страницы в пагинатор.

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию:
```
@CODE: <a href="[+link+]" class="page">[+num+]</a>
```

###TplCurrentPage  

Шаблон оформления текущей страницы в пагинаторе 

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию:
```
@CODE: <b class="current">[+num+]</b>
```

###TplWrapPaginate 

Шаблон контейнер для обертки страниц пагинации.

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию:
```
@CODE: <div class="[+class+]">[+wrap+]</div>
```

###pageLimit

Число страниц отображаемое в пагинаторе.

Возможные значения - целое число больше ноля.

Значение по умолчанию - 1.

###pageAdjacents

Максимальное число страниц слева и справа относительно текущей страницы.

Возможные значения - целое число больше ноля.

Значение по умолчанию - 4.

###PaginateClass

Класс для контейнера в который будут вложены страницы пагинации.

Возможные значения - любая строка сформированная по правилам для подстановки в HTML аттрибут тегов class.

Значение по умолчанию - paginate.

###PrevNextAlwaysShow

Всегда показывать "следующая страница" и "предыдущая страница".

Возможные значения - 1 или 0.

Значение по умолчанию - 0.

###TplFirstI

Шаблон для вставки ссылки "первая страница", используется совместно с PrevNextAlwaysShow.

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию: пусто.

###TplLastI

Шаблон для вставки ссылки "последняя страница", используется совместно с PrevNextAlwaysShow.

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию: пусто.

###TplNextI

Шаблон для вставки неактивной ссылки "следующая страница", используется совместно с PrevNextAlwaysShow. 

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию:
```
@CODE: [%paginate.next%] >
```

###TplPrevI

Шаблон для вставки неактивной ссылки "предыдущая страница", используется совместно с PrevNextAlwaysShow. 

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию:
```
@CODE: < [%paginate.prev%]
```

###TplDotsPage

Шаблон прострела.

Возможные значения - имя шаблона указанное по правилам задания шаблонов в DocLister.

Значение по умолчанию:
```
@CODE: ...
```

###noRedirect

Запрещает переадресацию при запросе несуществующей страницы.

Возможные значения - 0 или 1.

Значение по умолчанию - 0.

##Вывод в плейсхолдеры

###contentPlaceholder

Установка значений документов в персонализованные плейсхолдеры.

Возможные значения - 0, 1. Если значение параметра равно 1, то DocLister создает плейсхолдеры вида [+id.item[x]+]. Где x это порядковый номер документа в списке, а id это значение параметра id (см. описание параметра id).

Значение по умолчанию - 0

##API-режим

###api

Используется для формирования выдачи в формате JSON. 

Возможные значения - 0, 1 или список полей выбираемых документов.

Значение по умолчанию - 0.

###JSONformat

По какому принципу формировать JSON-ответ.

Возможные значения - old, new. В формате old ответ выглядит в виде обычного массива. В формате new ответ заворачивается в rows секцию + добавляется примесь total в которой указано общее число учавствующих в выборке

Значение по умолчанию - old.