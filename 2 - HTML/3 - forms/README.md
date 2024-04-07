# Конспект "Работа с формами"
### Формы
Формы в **html** представляют один из способов для ввода и отправки данных. Все поля формы помещаются между тегами `<form>` и `</form>`:

[В контексте](./src/form.html)
```html
<body>
    <form method="post" action="http://localhost:8080/login.php">
        <input name="login"/>
        <input type="submit" value="Войти" />
    </form>
</body>
```
> Для настройки форм у элемента `form` определены следующие атрибуты:
> - `method`: устанавливает метод отправки данных на сервер. Допустимы два значения: post и get.
> > Значение post позволяет передать данные на веб-сервер через специальные заголовки. А значение get позволяет передать данные через строку запроса.
> - `action`: устанавливает адрес, на который передаются данные формы
> - `enctype`: устанавливает тип передаваемых данных. Он свою очередь может принимать следующие значения:
>   - `application/x-www-form-urlencoded`: кодировка отправляемых данных по умолчанию
>   - `multipart/form-data`: эта кодировка применяется при отправке файлов
>   - `text/plain`: эта кодировка применяется при отправке простой текстовой информации
> -  `autocomplete`: устанавливает возможность автодополнения поля 

#
### Элементы Форм
Значения атрибута `type` элемента `input`:
- `text`: обычное текстовое поле
- `password`: тоже текстовое поле, только вместо вводимых символов отображаются звездочки, поэтому в основном используется для ввода пароля
- `radio`: радиокнопка или переключатель. Из группы радиокнопок можно выбрать только одну
- `checkbox`: элемент флажок, который может находиться в отмеченном или неотмеченном состоянии
- `hidden`: скрытое поле
- `submit`: кнопка отправки формы
- `color`: поле для ввода цвета
- `date`: поле для ввода даты
- `datetime`: поле для ввода даты и времени с учетом часового пояса
- `datetime-local`: поле для ввода даты и времени без учета часового пояса
- `email`: поле для ввода адреса электронной почты
- `month`: поле для ввода года и месяца
- `number`: поле для ввода чисел
- `range`: ползунок для выбора числа из некоторого диапазона
- `tel`: поле для ввода телефона
- `time`: поле для ввода времени
- `week`: поле для ввода года и недели
- `url`: поле для ввода адреса url
- `file`: поле для выбора отправляемого файла
- `image`: создает кнопку в виде картинки
> Кроме элемента `input` в различных модификациях есть еще небольшой набор элементов, которые также можно использовать на форме:
> - `button`: создает кнопку
> - `select`: выпадающий список
> - `label`: создает метку, которая отображается рядом с полем ввода
> - `textarea`: многострочное текстовое поле

#
### Кнопки
Кнопки представлены элементом `button`. Значения атрибута `type`:
- `submit`: кнопка, используемая для отправки формы
- `reset`: кнопка сброса значений формы
- `button`: кнопка без какого-либо специального назначения

> Если кнопка используется для отправки формы, то есть у нее установлен атрибут `type="submit"`, то мы можем задать у нее ряд дополнительных атрибутов:
> - `form`: определяет форму, за которой закреплена кнопка отправки
> - `formaction`: устанавливает адрес, на который отправляется форма. Если у элемента form задан атрибут action, то он переопределяется
> - `formenctype`: устанавливает формат отправки данных. Если у элемента form установлен атрибут enctype, то он переопределяется
> - `formmethod`: устанавливает метод отправки формы (post или get). Если у элемента form установлен атрибут method, то он переопределяется

Пример кнопок в HTML:

[В контексте](./src/button.html)
```html
<form>
    <p>
        <button type="submit" formmethod="get" formaction="index.html">Отправить</button> 
        <button type="reset">Отмена</button>
    </p>
</form>
```

> Кроме элемента `button` для создания кнопок можно использовать элемент `input`, у которого атрибут равен `submit` или `reset`. Например:
>
> [В контексте](./src/button.html)
> ```html
> <form>
>     <p>
>         <input type="submit" formmethod="get" formaction="index.html" value="Отправить"/>
>         <input type="reset" value="Отмена"/>
>     </p>
> </form>
> ```

И еще один элемент input с атрибутом type="image" позволяет использовать в качестве кнопки изображение:

[В контексте](./src/button.html)
```html
<form>
    <p>
        <input type="text" name="search" />
        <input type="image" src="search.png" name="submit" />
    </p>
</form>
```

#
### Текстовые поля
Однострочное текстовое поле создается с помощью элемента `input`, когда его атрибут `type` имеет значение `text`:
```html
<form>
    <input type="text" name="login" />
</form>
```

Атрибуты текстового поля:
- `dir`: устанавливает направление текста
- `list`: устанавливает список подсказок для ввода в поле
- `maxlength`: максимально допустимое количество символов в текстовом поле
- `pattern`: определяет шаблон, которому должен соответствовать вводимый текст
- `placeholder`: устанавливает текст, который по умолчанию отображается в текстовом поле
- `readonly`: делает текстовом поле доступным только для чтения
- `disabled`: делает текстовом поле доступным только для чтения и затемняет поле
- `required`: указывает, что текстовое поле обязательно должно иметь значение
- `size`: устанавливает ширину текстового поля в видимых символах
- `value`: устанавливает значение по умолчанию в текстовом поле

> Для создания полей поиска предназначен элемент `input` с атрибутом `type="search"`. Формально он представляет собой простое текстовое поле.
>
> Для ввода пароля используется элемент `input` с атрибутом `type="password"`. Его отличительной чертой является то, что вводимые символы маскируются точками.

Среди атрибутов текстового поля также следует отметить такой атрибут как `list`. Он содержит ссылку на элемент `datalist`, который определяет набор значений, появляющихся в виде подсказки при вводе в текстовое поле. Например:

[В контексте](./src/text_field.html)
```html
<body>
    <form>
        <p><input list="phonesList" type="text" name="model" placeholder="Введите модель" /></p>
        <p>
            <button type="submit">Отправить</button>
        </p>
    </form>
    <datalist id="phonesList">
        <option value="iPhone 6S" label="54000"/>
        <option value="Lumia 950">35000</option>
        <option value="Nexus 5X"/>
    </datalist>
</body>
```

#
### Метки и автофокус
Вместе с полями ввода нередко используются метки, которые представлены элементом `label`. Метки создают аннотацию или заголовок к полю ввода, указывают, для чего это поле предназначено.

Для связи с полем ввода метка имеет атрибут `for`, который указывает на `id` поля ввода:

[В контексте](./src/label.html)
```html
<form>
    <p>
        <label for="login">Логин: </label>
        <input type="text" id="login" name="login" />
    </p>
    <p>
        <label for="password">Пароль: </label>
        <input type="password" id="password" name="password" />
    </p>
    <p>
        <button type="submit">Отправить</button>
    </p>
</form>
```
> Также в `input` можно применить атрибут `autofocus`, для автофокуса по умолчанию.

#
### Элементы для ввода чисел
Для ввода чисел используется элемент `input` с атрибутом `type="number"`. Он создает числовое поле, которое мы можем настроить с помощью следующих атрибутов:
- `min`: минимально допустимое значение
- `max`: максимально допустимое значение
- `readonly`: доступно только для чтения
- `required`: указывает, что данное поле обязательно должно иметь значение
- `step`: значение, на которое будет увеличиваться число в поле
- `value`: значение по умолчанию

[В контексте](./src/numeric_field.html)

```html
<form>
    <p>
        <label for="age">Возраст: </label>
        <input type="number" step="1" min="1" max="100" value="10" id="age" name="age"/>
    </p>
    <p>
        <button type="submit">Отправить</button>
    </p>
</form>
```

> Как и в случае с текстовым полем мы можем здесь прикрепить список `datalist` с диапазоном возможных значений:
>
> [В контексте](./src/numeric_field.html)
> ```html
> <form>
>     <p>
>         <label for="price">Цена: </label>
>         <input type="number" list="priceList"
>             step="1000" min="3000" max="100000" value="10000" id="price" name="price"/>
>     </p>
>     <p>
>         <button type="submit">Отправить</button>
>     </p>
> </form>
> <datalist id="priceList">
>     <option value="15000" />
>     <option value="20000" />
>     <option value="25000" />
> </datalist>
> ```

Ползунок представляет шкалу, на которой мы можем выбрать одно из значений. Для создания ползунка применяется элемент `input` с атрибутом `type="range"`. Во многом ползунок похож на простое поле для ввода чисел. Он также имеет атрибуты `min`, `max`, `step` и `value`:

[В контексте](./src/numeric_field.html)
```html
<form>
    <p>
        <label for="price">Цена:</label> 
        1<input type="range" step="1" min="0" max="100" value="10" id="price" name="price"/>100
    </p>
    <p>
        <button type="submit">Отправить</button>
    </p>
</form>
```

#
### Флажки и переключатели
Флажок представляет элемент, который может находиться в двух состояниях: отмеченном и неотмеченном. Флажок создается с помощью элемента `input` с атрибутом `type="checkbox"`:

[В контексте](./src/checkboxes_radio.html)
```html
<form>
    <p>
        <input type="checkbox" checked name="html5"/>HTML5
    </p>
    <p>
        <input type="checkbox" name="dotnet"/>.NET
    </p>
    <p>
        <input type="checkbox" name="java"/>Java
    </p>
    <p>
        <button type="submit">Отправить</button>
    </p>
</form>
```

Переключатели или радиокнопки похожи на флажки, они также могут находиться в отмеченном или неотмеченном состоянии. Только для переключателей можно создать одну группу, в которой одновременно можно выбрать только один переключатель. Например:

[В контексте](./src/checkboxes_radio.html)
```html
<form>
    <p>
        <input type="radio" value="man" checked name="gender"/>мужской
    </p>
    <p>
        <input type="radio" value="woman" name="gender"/>женский
    </p>
</form>
```

#
### Элементы для ввода информации
За установку цвета в HTML5 отвечает специальный элемент `input` с типом `color`:

[В контексте](./src/input_info.html)
```html
<body>
    <label for="favcolor">Выберите цвет</label>
    <input type="color" id="favcolor" name="favcolor" />
</body>
```
> С помощью элемента `datalist` мы можем задать набор цветов, из который пользователь может выбрать нужный:
> 
> [В контексте](./src/input_info.html)
> ```html
> <label for="favcolor">Выберите цвет</label>
> <input type="color" list="colors" id="favcolor" name="favcolor" />
> <datalist id="colors">
>     <option value="#0000FF" label="blue">
>     <option value="#008000" label="green">
>     <option value="#ff0000" label="red">
> </datalist>
> ```

Чтобы создать поле для ввода электронной почты используется:

[В контексте](./src/input_info.html)
```html
<label for="email">Email: </label>
<input type="email" placeholder="user@gmail.com" id="email" name="email"/>
```

Чтобы создать поле для ввода URL используется:

[В контексте](./src/input_info.html)
```html
<label for="url">URL: </label>
<input type="url" id="url" name="url"/>
```

Чтобы создать поле для ввода телефона используется:

[В контексте](./src/input_info.html)
```html
<label for="phone">Телефон: </label>
<input type="tel" placeholder="(XXX)-XXX-XXXX" id="phone" name="phone"/>
```
> Для их настройки мы можем использовать те же атрибуты, что и для обычного текстового поля:
> - `maxlength`: максимально допустимое количество символов в поле
> - `pattern`: определяет шаблон, которому должен соответствовать вводимый текст
> - `placeholder`: устанавливает текст, который по умолчанию отображается в поле
> - `readonly`: делает текстовом поле доступным только для чтения
> - `required`: указывает, что текстовое поле обязательно должно иметь значение
> - `size`: устанавливает ширину поля в видимых символах
> - `value`: устанавливает значение по умолчанию для поля
> - `list`: устанавливает привязку к элементу `datalist` со списком возможных значений

#
### Элементы для ввода даты и времени
Для работы с датами и временем в HTML5 предназначено несколько типов элементов `input`:
- `datetime-local`: устанавливает дату и время
- `date`: устанавливает дату
- `month`: устанавливает текущий месяц и год
- `time`: устанавливает время
- `week`: устанавливает текущую неделю

[В контексте](./src/data_time.html)
```html
<form>
    <p>
        <label for="date">Дата: </label>
        <input type="date" id="date" name="date"/>
    </p>
    <p>
        <label for="week">Неделя: </label>
        <input type="week" name="week" id="week" />
    </p>
    <p>
        <label for="localdate">Дата и время: </label>
        <input type="datetime-local" id="localdate" name="date"/>
    </p>
    <p>
        <label for="month">Месяц: </label>
        <input type="month" id="month" name="month"/>
    </p>
    <p>
        <label for="time">Время: </label>
        <input type="time" id="time" name="time"/>
    </p>
</form>
```

#
### Отправка файлов
За выбор файлов на форме отвечает элемент `input` с атрибутом `type="file"`:

[В контексте](./src/file.html)
```html
<form enctype="multipart/form-data" method="post" action="http://localhost:8080/postfile.php">
    <input type="file" name="file" />
</form>
```
> Важно отметить, что для отправки файла на сервер форма должна иметь атрибут `enctype="multipart/form-data"`.
> С помощью ряда атрибутов мы можем дополнительно настроить элементы выбора файла:
> - `accept`: устанавливает тип файл, которые допустимы для выбора
> - `multiple`: позволяет выбирать множество файлов
> - `required`: требует обязательной установки файла
> ```html
> <form enctype="multipart/form-data" method="post" action="http://localhost:8080/postfile.php">
>   <input type="file" name="file" multiple />
> </form>
> ```

#
### Список select
Элемент select создает список. В зависимости от настроек это может быть выпадающий список для выбора одного элемента, либо раскрытый список, в котором можно выбрать сразу несколько элементов:

[В контексте](./src/select.html)
```html
<form method="get">
    <p>
        <label for="phone">Выберите модель:</label>
        <select id="phone" name="phone">
            <option value="iphone 6s">iPhone 6S</option>
            <option value="lumia 950">Lumia 950</option>
            <option value="nexus 5x">Nexus 5X</option>
            <option value="galaxy s7">Galaxy S7</option>
        </select>
    </p>
</form>
```

`Select` также позволяет группировать элементы с помощью тега `<optgroup>`:

[В контексте](./src/select.html)
```html
<form method="get">
    <p>
        <label for="phone">Выберите модель:</label>
     
        <select id="phone" name="phone">
            <optgroup label="Apple">
                <option value="iphone 6s">iPhone 6S</option>
                <option value="iphone 6s plus">iPhone 6S Plus</option>
                <option value="iphone 5se">iPhone 5SE</option>
            </optgroup>
            <optgroup label="Microsoft">
                <option value="lumia 950">Lumia 950</option>
                <option value="lumia 950 xl">Lumia 950 XL</option>
                <option value="lumia 650">Lumia 650</option>
            </optgroup>
        </select>
    </p>
</form>
```
> Для создания списка с множественным выбором к элементу `select` надо добавить атрибут `multiple`.
>
> С помощью другого атрибута `disabled` можно запретить выбор определенного элемента. Как правило, элементы с этим атрибутом служат для создания заголовков.

#
### Textarea
Чтобы создать многострочное текстовое поле используют элемент `textarea`:

```html
<form method="get">
    <p>
        <label for="comment">Ваш комментарий:</label><br/>
        <textarea name="comment" id="comment" placeholder="Не более 200 символов" maxlength="200"></textarea>   
    </p>
</form>
```
> С помощью дополнительных атрибутов `cols` и `rows` можно задать соответственно количество столбцов и строк.

#
### Валидация форм
Для создания валидации у элементов форм `HTML5` используется ряд атрибутов:
- `required`: требует обязательного ввода значения. Для элементов `textarea`, `select`, `input` (с типом `text`, `password`, `checkbox`, `radio`, `file`, `datetime-local`, `date`, `month`, `time`, `week`, `number`, `email`, `url`, `search`, `tel`)
- `min` и `max`: минимально и максимально допустимые значения. Для элемента `input` с типом `datetime-local`, `date`, `month`, `time`, `week`, `number`, `range`
- `pattern`: задает шаблон, которому должны соответствовать вводимые данные. Для элемента `input` с типом `text`, `password`, `email`, `url`, `search`, `tel`

[В конексте](./src/validation.html)

> Атрибут `novalidate`, либо у кнопки отправки атрибут `formnovalidate` отвечают за выключение обязательной валидации

#
### Элементы fieldset и legend
Для группировки элементов формы нередко применяется элемент `fieldset`. Он создает границу вокруг вложенных элементов, как бы создавая из них группу. Вместе с ним используется элемент `legend`, который устанавливает заголовок для группы элементов.

[В конексте](./src/fieldset.html)

#

[HTML5](../README.md)