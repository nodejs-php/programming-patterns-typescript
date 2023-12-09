# Паттерн "Команда"

### Цель

Нужно запросы превратить в объекты и выполнить како-то действие

### Реализация

1. Создается интерфейс команды ``interface ICommand`` с методом ``execute(): void``.
2. Создаются классы, реализующие данный интерфейс ``interface ICommand``. Это команды
3. Создается большой класс ``Invoker`` для вызова команд. В данном классе имеется хеш команд
   ``#commands: { [index: string] }`` для доступа с ключом-индексом к командам. В него же можно добавить массив
   истории команд ``#history: [number, string][]``. У класса ``Invoker`` имеются методы регистрации команд в хеше
   ``#commands``

 ```ts
function register(commandName: string, command: ICommand): void {
    #command[commandName] = command
}
```

Имеется также метод вызова команды

 ````ts
function execute(commandName: string): void {
    #command[commandName].execute()
}
````

При использовании происходит регистрация команд в объекте и запуск по имени команды.