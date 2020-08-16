1. In `components` create a folder called `CookieList`, inside it create an `index.js` file and setup your component.

2. Also create a `CookieItem.js` file and setup your component.

3. In `index.js`, map over `cookies` in `cookieStore` and pass every `cookie` to `CookieItem`.

    ```javascript
    const cookieList = cookieStore.cookies.map(
        (cookie) => (<CookieItem cookie={cookie} key={cookie.id} />)
    );
    ```

4. Render `cookieList` in a `List` component within a `Content` component.
   
    ```javascript
    return (
        <Content>
            <List>{cookieList}</List>
        </Content>
    );
    ```

5. In `Cookie`, let's render the name of the `cookie`. Pass `cookie` as a `prop`, import `BakeryItemStyled` from `BakeryList/styles` and render `cookie.name`.

    ```javascript
    import React from "react";
    import { BakeryItemStyled } from "../BakeryList/styles";

    const CookieItem = ({ cookie }) => {
        return <BakeryItemStyled>{cookie.name}</BakeryItemStyled>;
    };

    export default CookieItem;
    ```

6. Temporarily in `App.js`, comment out `BakeryList` and render `CookieList`.
