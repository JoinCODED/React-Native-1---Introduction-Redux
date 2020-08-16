1. In `components` create a folder called `BakeryList`, inside it create an `index.js` file and setup your component.

2. Also create a `BakeryItem.js` file and setup your component.

3. In `index.js`, map over `bakeries` in `bakeryStore` and pass every `bakery` to `BakeryItem`.

    ```javascript
    const bakeryList = bakeryStore.bakeries.map(
        (bakery) => (<BakeryItem bakery={bakery} key={bakery.id} />)
    );
    ```

4. Render `bakeryList` in a `View` component.
   
    ```javascript
    return <View>{bakeryList}</View>;
    ```

5. For now in `BakeryItem`, let's just render the name of the `bakery`. Pass `bakery` as a `prop`, import `Text` from `react-native` and render `bakery.name`.

    ```javascript
    import React from "react";
    import { Text } from "react-native";

    const BakeryItem = ({ bakery }) => {
    return <Text>{bakery.name}</Text>;
    };

    export default BakeryItem;
    ```

6. Temporarily in `App.js`, comment out `Home` and render `BakeryList`.

7. Note that the items are not always showing, let's add an `observer` to `BakeryList`.

    ```javascript
    export default observer(BakeryList);
    ```

8. Also let's add the `loading` condition here. If `loading` is true, render a `Text` saying `Loading...`.

    ```javascript
    if (bakeryStore.loading) return <Text>Loading...</Text>
    ```


