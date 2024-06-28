## Задача 2: Работяга
Описание
В данной задаче вам необходимо реализовать класс Worker, который будет выполнять некоторые задачи и возвращать результат в родительский класс Main.

public class Worker {

}
Для того, чтобы класс Worker мог вернуть результат своей работы, реализуйте собственный функциональный интерфейс OnTaskDoneListener. В нем определите только один метод onDone() без реализации и пометьте интерфейс аннотацией @FunctionalInterface:

@FunctionalInterface
public interface OnTaskDoneListener {
    void onDone(String result);
}
Добавьте в класс Worker переменную callback типа OnTaskDoneListener:

private OnTaskDoneListener callback;
Передайте в класс Worker ее значение через конструктор:

public Worker(OnTaskDoneListener callback) {
    this.callback = callback;
}
Смоделируйте выполнение классом Worker какой либо работы, например:

public void start() {
    for (int i = 0; i < 100; i++) {
        callback.onDone("Task " + i + " is done");
    }
}
Обратите внимание на то, что каждая итерация цикла означает выполнение задачи, результат который передается через метод onDone() функционального интерфейса OnTaskDoneListener.

Реализация
В классе Main в методе main() определите переменную listener типа OnTaskDoneListener через лямбда-выражение:

OnTaskDoneListener listener = System.out::println;
Далее создайте экземпляр класса Worker и передайте в конструктор класса listener:

Worker worker = new Worker(listener);
worker.start();
Обратите внимание на консоль. Все предполагаемые 100 задач были выполнены успешно.