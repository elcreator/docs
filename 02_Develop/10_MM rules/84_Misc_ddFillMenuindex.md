Описание
Виджет для плагина ManagerManager, выставляющий минимальное свободное значение позиции меню (menuindex) для новых документов. По умолчанию позиция меню в MODx для новых документов просто равна количеству дочерних документов на одном уровне, что не всегда удобно.
Список изменений
Первая версия.
Документация
Для установки распакуйте архив в /assets/plungins/managermanager/widgets/. Смотрите также документацию ManagerManager 0.5 и модуль ddMMEditor.
Описание параметров
Название	Описание	Допустимые значения	Значение по умолчанию	Обязателен?
parent	ID документа, для дочерних документов которого должен применяться виджет. Если оставить пустым (не указаывать), то виджет будет применён абсолютно ко всем документам.	{integer; ''}	—	false