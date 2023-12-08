# Абстрактная фабрика
Нужно чтобы получать создавать и получать объекты в зависимости от каких-то параметров

1. Сначала пишутся интерфейсы с описанием переменных и их типов в отдельных модулях.
``export interface IObject``, ``export class ObjectClass implements IObject``. 
Переменные в них ``variable: string``, ``function action()``. Могут также испортироваться типы
переменных с другого модуля, описанных ``type export type variableType = { ... }`` и импортированных 
``import { variableType } from ...``

2. Пишется абстрактные фабрики, которые описываются в виде классов ``class SomeFactory { ... }`` и в 
них имеется статический метод создания или получения объектов абстрактной фабрики описанной в виде классов.
Абстрактные фабрики могут быть вложенными друг в друга и могут использоваться в других абстрактных фабриках. 
При создании объектов могут использоваться условия ``if``. Если класс объекта с данным параметром не найден 
то созадется и выбрасывается исключение ``Exception``
