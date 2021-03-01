1. In `components` create a file called `BakeryList.js` and setup your component.

2. Also create a `BakeryItem.js` file and setup your component.

3. In `BakeryList.js`, import `useSelector` and fetch all `bakeries` from the bakery reducer.

   ```javascript
   const bakeries = useSelector((state) => state.bakeryReducer.bakeries);
   ```

4. Map over `bakeries` and pass every `bakery` to `BakeryItem`.

   ```javascript
   const bakeryList = bakeries.map((bakery) => (
     <BakeryItem bakery={bakery} key={bakery.id} />
   ));
   ```

5. Render `bakeryList` in a `View` component.

   ```javascript
   return <View>{bakeryList}</View>;
   ```

6. For now in `BakeryItem`, let's just render the name of the `bakery`. Pass `bakery` as a `prop`, import `Text` from `react-native` and render `bakery.name`.

   ```javascript
   import React from "react";
   import { Text } from "react-native";

   const BakeryItem = ({ bakery }) => {
     return <Text>{bakery.name}</Text>;
   };

   export default BakeryItem;
   ```

7. Temporarily in `App.js`, comment out `Home` and render `BakeryList`.

8. Also let's add the `loading` condition here. Fetch `loading` from the `shopReducer`.

   ```javascript
   const loading = useSelector((state) => state.bakeryReducer.loading);
   ```

9. If `loading` is true, render a `Text` saying `Loading...`.

   ```javascript
   if (loading) return <Text>Loading...</Text>;
   ```
