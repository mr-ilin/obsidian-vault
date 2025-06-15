https://varun04tomar.medium.com/open-nuts-and-bolts-of-memory-management-in-ios-swift-part-1-4927b60fccf8
In simple words, memory is a collection of bytes, every byte have it’s own address. If we talk in terms of programming then, range of these byte addresses called as address space. An address space can consist of following components : “_text_”, “_data_”, “_heap_” and “_stack_”.

1. **_text_** segment contains machine instructions that form the app’s executable code.
2. **_data_** segment stores Swift static variables, constants and type metadata.
3. **_stack_** is used for local scoped variables and value types(with some exception), it contains method parameters and local variables.
4. **_heap_** is for objects those have a lifetime, it’s mainly used for the reference type variables with some value type exception. (We will discuss later)
![memory](https://miro.medium.com/v2/resize:fit:408/format:webp/1*OcBOBxc1Ivr7eTJFur9PaQ.png)

https://habr.com/ru/articles/191058/
Когда мы компилируем исходный файл, на выходе мы получаем файл объектный, который типично содержит в себе несколько секций с данными. Четыре самые распространенные секции это:  

- **.text** — скомпилированный машинный код;
- **.data** — глобальные и статические переменные;
- **.rodata** — аналог `.data` для неизменяемых данных;
- **.bss** — глобальные и статические переменные, которые при старте содержат нулевое значение.