### Links

-   [Layout](https://www.figma.com/file/uBaU2XAC6gZqtshk59mMHL)
-   [Task](https://docs.google.com/document/d/1cYDhmM4o0st7mGylsOIlxyVC3gZyNtAb/edit)

### Deps

-   Vue 3 composition api
-   Javascript
-   CSS modules

### Run

##### Dev

```sh
npm run dev
```

##### Preview

```sh
npm run build && npm run preview
```

### Javascript Tasks

1. Выполнится приведение типов к строке и конкатенация
    ```js
    console.log([1, 2, 3] + [4, 5, 6]) // '1,2,34,5,6'
    ```
2. Присваивание объектов происходит по ссылке. (в переменной `b` лежит ссылка на значение `a`)

    ```js
    var a = { b: 1 }
    var b = a

    b.b = 2

    console.log(a) // { b: 2 }
    ```

3. Не пропускает `00.1`, `0.0.1`, `0.1000`
    ```js
    /(0|[1-9]\d*)([.,])([0-9]{1,3})/g
    ```
4. Строка проверяется на наличие:

    - `https или http` и `://`
    - `www.`
    - host'а
    - path'а
    - query
    - anchor'а

    ```js
    /(https|http):\/\/(www\.)?([-a-zA-Z0-9]+\.)+([a-z]{2,6}(:\d+)?)(\/[a-zA-Z0-9]*)*(\?[a-zA-Z0-9@:%_+.~#?&/=-]*)?/g
    ```

5. Function и var имеют механизм hoisting'а, поэтому доступны до своего объявления

    ```js
    function setText(message) {
        text = message
    }

    var text = 'Текст'

    console.log(setText('Сообщение')) // 'Сообщение'
    ```

6. Возвращает массив артикулов строкового типа

    ```js
    /** @return {(string|null)[]} */
    function getVendorList() {
        const productList = document.querySelectorAll('._product')

        return Array.from(productList).map((product) => product.dataset?.id ? `0${product.dataset.id}` : null)
    }
    ```

7. Возвращает объект с ключом и значением строкового типа

    ```js
    /** @return {Record<string, string>} */
    function getProperties() {
        const properties = {}

        const namePropertyList = document.querySelectorAll('.parameter-name')
        const valuePropertyList = document.querySelectorAll('.parameter-name ~ .parameter-value')

        for (const [i, nameProperty] of namePropertyList.entries()) {
            properties[nameProperty.firstChild.textContent.trim()] = valuePropertyList[i].firstChild.textContent.trim()
        }

        return properties
    }
    ```
