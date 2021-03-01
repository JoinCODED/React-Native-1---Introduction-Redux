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

4. Render `cookieList` in a `List` component within a `Content` component.

   ```javascript
   return (
     <Content>
       <List>{cookieList}</List>
     </Content>
   );
   ```

5. In `CookieItem`, let's render the name and the image of the `cookie`. Pass `cookie` as a `prop`, import `BakeryItemStyled` and render them.

   ```javascript
   import React from "react";
   import { BakeryItemStyled } from "../styles";
   import { ListItem } from "native-base";
   import { Image } from "react-native";

   const CookieItem = ({ cookie }) => {
     return (
       <ListItem>
         <Image
           style={{ width: "100px", height: "100px" }}
           source={{ uri: cookie.image }}
         />
         <BakeryItemStyled>{cookie.name}</BakeryItemStyled>
       </ListItem>
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
       <>
         <BakeryDetailWrapper>
           [...]
         </BakeryDetailWrapper>
         <CookieList cookies={cookiesFromCookieStore} />
       </>
     );
   };
   ```

7. You should now see this bakery's list of cookies!
