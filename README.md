Привет, данное тестовое задание состоит из этапов, которые надо проходить в четкой последовательности. Есть бонусные пункты. Если очень хотите к нам — сделайте второй подход, и реализуйте их также.

После завершения каждого этапа делайте коммит, чтоб можно было посмотреть историю развития вашего апп.

Отдать работу надо ссылкой на гитхаб, чтобы была возможность запустить ваше решение и проверить его логику.

Вам предоставлен файл sdk.js в нём есть весь вспомогательный функционал, ИЗМЕНЯТЬ ФАЙЛ ЗАПРЕЩЕННО.

Технические требования
  1. Нужно выбрать state manager (Redux/mobx/react-query) или можете использовать только апи реакта, но будет бонус если возьмете Redux
  2. Компоненты реакт в функциональном стиле
  3. Все компоненты должны иметь описания пропсов (prop-types)
  4. Дриллить пропсы можно максимум на одну вложеность.

# Цель задачи
  Построить приложение, которое будет логинить пользователя в систему, и, после успешного входа, показывать список его билетов.

## Этап 1
  Нам нужо подготовить среду в которой мы будем писать код, можно взять готовую на ваш вкус например create react app
  _Если напишете своё решение, это будет большим плюсом_

## Этап 2
  Нам нужно создать базовый скелет приложения, разбить страницу входа на компоненты, можно подключить ui библиотеку чтоб ваше решение выглядило красиво.

## Этап 3
  Начинаем программировать форму. На данном этапе нужно реализовать:
    1. Контроль состояни инпутов email, password.
    2. Бонус! Валидация данных полей.
      2.1 Email проверка на корректность поля и на заполненость
      2.2 Проверка пароля не меньше 3 символов.
    3. Бонус! Вывод ошибок валидации под поля.
    4. Отправку данных в метод authenticateUser(email, password)
      4.1 Обработать успешный вызов асинхроной функции и ошибку
      4.2 Если успех, сделать редирект на главную страницу апп
      4.3 Если ошибка показать ошибку под формой (вывести ошибку от API)

## Этап 4
  Внедряем новую фичу в форму, запоминание авторизации
  1. Нужно добавить в форму чекбокс «Запомнить меня», который будет отвечать за данную логику.
  2. При авторизации, если чекбокс установлен, токен надо сохранить в Local storage.
   2.1 Бонус! Обработать кейс если юзер запретил доступ к хранилищам браузера.
  3. При загрузке апп нужно проверить наличие токена в сторедже, и, если он есть, проверить его на валидность.
    3.1 используем метод validateToken(token)
    3.2 если токен валидный, делаем вызов метода для получения юзера по токену getUser(token) получаем юзера
    3.3 делаем редирект на главную страницу, если все ок
    3.4 обрабатываем ошибку, редирект на логин и ошибка на ваш вкус

## Этап 5
  Делаем правильный роутинг по апп
  1. Для авторизированого юзера страница логина закрыта, это нужно проверять и выкидывать на главную.
    1.1 Бонус! Делать редирект не просто на главную, а прочитать с URL квери параметр ?redirect=customURL
  2. Для не авторизированого юзера все маршруты апп закрыты и при попытке перехода выкидываем на страницу логина
  3. Бонус! Доработать логику авторизации, дописать редирект не просто на главную страницу апп, а посмотреть URL и проверить нет ли там ?redirect=customURL

## Этап 6
  Делаем главную страницу со списком билетов.
  1. Добавить хедер в котором есть:
    1.1 Email юзера.
  2. Добавить компонент с билетами юзера.
    2.1 Создать разметку для компонента.
    2.2 Загрузить авиа билеты с помощью метода getFlights(token)
    2.3 Отсортировать их по дате.
    2.4 Вывести информацию про название авиакомпании, дату вылета.
  3. Добавить сверху билетов поиск по названию компании.
    3.1 Ловим события ввода в инпунт и делаем поиск по именам.
    3.2 Поиск идет сначало по имени, потом по альтернативным именам.
    3.3 Учесть регистры символов.

## Этап 7
  Добавляем фичу в хедер, кнопка выхода с системы
  1. Делаем полный сброс приложения и редирект на страницу логина
