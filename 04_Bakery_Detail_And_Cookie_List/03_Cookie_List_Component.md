1. In `components` create a file called `CookieList.js` and setup your component.

2. Also create a `CookieItem.js` file and setup your component.

3. In `CookieList.js`, receive as a prop and map over `cookies` and pass every `cookie` to `CookieItem`.

   ```javascript
   const CookieList = ({ cookies }) => {
     const cookieList = cookies.map((cookie) => (
       <CookieItem cookie={cookie} key={cookie.id} />
     ));
   };
   ```

4. Render `cookieList` in a `VStack` component.

   ```javascript
   return <VStack space="5">{cookieList}</VStack>;
   ```

5. In `CookieItem`, let's render the name and the image of the `cookie`. Pass `cookie` as a `prop`, import `BakeryItemStyled` and render them.

   ```javascript
   import React from 'react';
   import { HStack } from 'native-base';
   import React from 'react';
   import { Text } from 'react-native';

   const CookieItem = ({ cookie }) => {
     return (
       <HStack w="100%" alignItems="center" space="3">
         <Image
           source={{
             uri: cookie.image,
           }}
           alt="image"
           style={{ width: 100, height: 100 }}
         />
         <Text>{cookie.name}</Text>
       </HStack>
     );
   };

   export default CookieItem;
   ```

6. In your `BakeryDetail`, import `useSelector` to get the bakery's cookies from the cookie reducer, and pass them to `CookieList`.

   ```javascript
   const BakeryDetail = () => {
     [...]
     const cookies = useSelector((state) => state.cookieReducer.cookies);

     const cookiesFromCookieStore = bakery.cookies.map((cookie) =>
       cookies.find(_cookie => (cookie.id === _cookie.id))
     );

      return (
    <View style={styles.BakeryDetailWrapper}>
      <Image
        style={styles.BakeryDetailImage}
        source={{ uri: bakery.image }}
      />
      <Text style={styles.BakeryDetailTitle}>{bakery.name}</Text>
      <BakeryList cookies={cookiesFromCookieStore} />
    </View>
   );
   };
   ```

7. You should now see this bakery's list of cookies!
