1. In the RN Debugger, you can see that `props` received by the `Home` component has something called `navigation` which has all the functions we need. This is the super power of React Navigation.

2. To navigate from one screen to another, we will use the `navigate` method of the `props.navigation` object.

3. In `Home.js`, receive `{navigation}` as a `prop`.

   ```jsx
   const Home = ({ navigation }) => {
   ```

4. Replace the `alert` in the `onPress` to navigate to the List Screen:

   ```jsx
   <ButtonStyled onPress={() => navigation.navigate()}>
     Click here to skip
   </ButtonStyled>
   ```

5. But what will we pass to `navigate`? The `name` of the screen we want to navigate to. Keep in mind that it has to be a string.

   ```jsx
   <ButtonStyled onPress={() => navigation.navigate("BakeryList")}>
     Click here to skip
   </ButtonStyled>
   ```

   Note that the navigation is animated, it affects the header by adding a back button which actually works, and you can go back using gestures! The magic of React Navigation!!!

6. Now whenever we press on a bakery, we want to go to the list of cookies. So let's add an `onPress` to our `ListItem` in `BakeryItem`.

   ```jsx
   const BakeryItem = ({ bakery, navigation }) => {
     return (
       <ListItem onPress={() => navigation.navigate("BakeryDetail")}>
         <BakeryItemStyled>{bakery.name}</BakeryItemStyled>
       </ListItem>
     );
   };
   ```

7. Oops. We got an error... Navigation won't work in `BakeryItem.js`. It is not part of the stack, thus it does not have access to `props.navigation`. In `BakeryList.js`, pass `navigation` as a `prop` to `BakeryItem`.

   ```jsx
   const BakeryList = ({ navigation }) => {
     [...]
     const bakeryList = bakeryStore.bakeries.map((bakery) => (
       <BakeryItem bakery={bakery} key={bakery.id} navigation={navigation} />
     ));
     [...]
   };
   ```
