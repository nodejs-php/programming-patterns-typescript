# Паттерн "Состояние"

### Цель

Объект должен менять свое поведение в зависимости от своего состояния

### Реализация

1. Создается интерфейс стратегии `interface IStrategy` с методом  `request` для выполнения особого алгоритма стратегии и
и создается его реализация класс-стратегия `ConcreteStrategy`
2. Создается интерфейс для конструктора стратегии который используется для передачи имени класса для конструирования
   новых объектов:
   ```ts
      interface IStrategyConstructor {
         // A Constructor for the IStrategy
         new(): IStrategy
      }
   ```
3. Создается контекстный объект стратегии `class ContextObject`, который включает
   метод `function method(strategyConstructor: IStrategyConstructor)`, который принимает как параметр конструктор
   класса, создает и возвращает новый объект
4. При выполнении алгоритма выполняется такой код с передачей стратегии-класса
````ts
const OBJECT_CONTEXT = new ObjectContext()
OBJECT_CONTEXT.request(ConcreteStrategy)
````