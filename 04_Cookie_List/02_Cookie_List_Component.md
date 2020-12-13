1. In `components` create a file called `CookieList.js` and setup your component.

2. Also create a `CookieItem.js` file and setup your component.

3. In `index.js`, map over `cookies` in `cookieStore` and pass every `cookie` to `CookieItem`.

   ```javascript
   const cookieList = cookieStore.cookies.map((cookie) => (
     <CookieItem cookie={cookie} key={cookie.id} />
   ));
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
           style={{ width: 100, height: 100 }}
           source={{ uri: cookie.image }}
         />
         <BakeryItemStyled>{cookie.name}</BakeryItemStyled>
       </ListItem>
     );
   };

   export default CookieItem;
   ```

6. Temporarily in `App.js`, comment out `BakeryList` and render `CookieList`.
