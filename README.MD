# Трекер задач

Реализован трекер задач для учета времени их выполнения. На базе фреймворка [Z8](https://github.com/zenframework/z8/) и с использованием [Z8 Template](https://github.com/zenframework/z8-template) реализованы основные функции. Описание фреймворка Z8, а также проекта Z8 Template приведено в [Wiki проекта Z8](https://github.com/zenframework/z8/wiki).

## Задание

1. С помощью фреймворка и языка BL разработать приложение "Трекер задач", содержащий основные сущности:
   - Проект - определяется наименованием и коротким уникальным кодом. Проекты связаны с пользователями (администратор определяет доступ к проекту для каждого конкретного пользователя).
   - Задача - создаётся в рамках проекта, определяется численным идентификатором (присваивается автоматически при создании), наименованием, текстовым описанием неограниченной длины, сложностью (трудоёмкостью в чел*часах), сроком исполнения, датой фактического исполнения, создателем (пользователем) и исполнителем (пользователем). У задачи есть статус - один из "Новая", "В работе", "Исполнена". Доступ на чтение определяется доступом текущего пользователя к проекту. Создатель и исполнитель могут редактировать задачу как угодно, кроме даты фактического исполнения. При изменении какого-либо поля задачи записывается история изменения: дата, автор изменения, измененный атрибут, новое значение. Создатель может удалить задачу, исполнитель - нет. Дата фактического исполнения задачи устанавливается автоматически в текущее время при выборе статуса "Исполнена", при смене статуса на иной дата исполнения сбрасывается.
   - Пользователь - определяется уникальным идентификатором (логином), паролем, именем. Использовать встроенный в Z8 класс Users.
2. Разработать представления данных (все представления доступны всем пользователям, но видимость и возможность редактирования конкретных записей определяются требованиями, описанными выше):
   - Все задачи - список всех задач в рамках всех проектов, доступных текущему пользователю. Представление должно содержать все поля задачи и все поля соответствующего проекта.
   - Мои задачи - как "Все задачи", но перечень задач ограничен только теми, в которых текущий пользователь является создателем или исполнителем.
   - Статистика - список всех пользователей с указанием количества созданных им задач, количества выполненных им задач, процент задач, выполненных в срок.

## Прогресс на данном этапе

- Разработаны основные сущности, но не реализовано:
> Доступ на чтение определяется доступом текущего пользователя к проекту. Создатель и исполнитель могут редактировать задачу как угодно, кроме даты фактического исполнения. При изменении какого-либо поля задачи записывается история изменения: дата, автор изменения, измененный атрибут, новое значение. Создатель может удалить задачу, исполнитель - нет.
- Представления данных в процессе разработки, но не реализовано:
> Все представления доступны всем пользователям, но видимость и возможность редактирования конкретных записей определяются требованиями.

## Z8 Template Project Build How-to

Copy _gradle.properties.default_ to _gradle.properties_ then choose one of project building options.

You have 2 options to develope Z8 porject:
1. Using Z8 Project sources from Git - _z8.home_ must point to Z8 Project folder, Gradle build script assumes Z8 Project is in Eclipse workspace
1. Using Z8 Project binaries - _z8Home_ must not be set

Eclipse workspace configuration:
1. If you use Z8 Project sources, Z8 Project must be in the same workspace.
1. If you use Z8 Project binaries, subproject _org.zenframework.z8.lang_ must be in the same workspace. Other Z8 dependencies are resolved with Gradle Maven plugin.
