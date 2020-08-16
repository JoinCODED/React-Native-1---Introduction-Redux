The styling is horrible! We need to fix the styling for our list to show. This sounds very exhausting. We need some bootstrap magic. But there's no Bootstrap in React Native, but there is something cooler called [Native Base](https://nativebase.io/).

1. Install `native-base`.

   ```shell
   $ yarn add native-base
   ```

2. In `BakeryList`, import `List` from `native-base`.

   ```javascript
   import { List } from "native-base";
   ```

3. Wrap `bakeryList` with `List` instead of `View`.

   ```javascript
   return <List>{bakeryList}</List>;
   ```

4. Now to fix it on top and bring it down a bit, add a `Content` component from `native-base`.

   ```javascript
   return (
     <Content>
       <List>{bakeryList}</List>
     </Content>
   );
   ```

   Much better!

5. Now let's style `BakeryItem`. Import `ListItem` from `native-base` and wrap `Text` with it. Amazing right?!

   ```javascript
   <ListItem>
     <Text>{bakery.name}</Text>
   </ListItem>
   ```

6. Note that you can scroll through it now.

7. Let's style the `Text` a bit. Create a `styles.js` file, import `styled` and create a new styled component for `Text`, and use it in `BakeryItem`.

   ```javascript
   export const BakeryItemStyled = styled.Text`
     color: ${(props) => props.theme.mainColor};
     font-size: 18;
     margin-top: 10;
     margin-bottom: 10;
   `;
   ```

8. Wow! This looks much better!

9. Another cool component from Native Base is the `Spinner`. Import it in `BakeryList` and render it instead of `Loading...`.

   ```javascript
   if (bakeryStore.loading) return <Spinner />;
   ```
