I miss styled components already! Can we use them with React Native components? Yes we can!

1. Install `styled-components`.

   ```shell
   $ yarn add styled-components
   ```

2. Import `ThemeProvider` in `App.js`.

   ```javascript
   import { ThemeProvider } from "styled-components";
   ```

3. Copy your `theme` object from your React app.

4. Wrap your `Home` component with the `ThemeProvider` and pass it the light or dark theme.

   ```javascript
   <ThemeProvider theme={theme.light}>
     <Home />
   </ThemeProvider>
   ```

5. Create a `styles.js` file.

6. Import `styled` from `styled-components/native`.

   ```javascript
   import styled from "styled-components/native";
   ```

7. Let's create a styled component for our `ImageBackground`, `View` and `Text` and move our styling.

   ```javascript
   export const HomeBackground = styled.ImageBackground`
     flex: 1;
     width: 100%;
     height: 100%;
   `;

   export const TopStyling = styled.View`
     height: 40%;
     align-items: center;
     justify-content: center;
   `;

   export const Title = styled.Text`
     color: #fff;
     font-size: 38;
     text-align: center;
   `;
   ```

8. Let's import them in `Home.js` and use them.

   ```javascript
   return (
     <HomeBackground
       source={{
         uri:
           "https://annabanana.co/wp-content/uploads/2020/03/Chocolate-Chip-Cookies-22.jpg",
       }}
     >
       <TopStyling>
         <Title>Cookies & Beyond</Title>
       </TopStyling>
     </HomeBackground>
   );
   ```

9. I want to add a colored but transparent layer on top of the image. Let's create a styled component of type `View`. We'll give it a `flex` and `backgroundColor`.

   ```javascript
   export const OverLayContainer = styled.View`
     flex: 1;
     background-color: rgba(100, 40, 60, 0.4);
   `;
   ```

10. Render it right under the `HomeBackground`

    ```javascript
    <HomeBackground
      source={{
        uri:
          "https://annabanana.co/wp-content/uploads/2020/03/Chocolate-Chip-Cookies-22.jpg",
      }}
    >
      <OverLayContainer>[...]</OverLayContainer>
    </HomeBackground>
    ```

11. Let's add a button that we can click on later to take us to the list of bakeries. In `styles`, create the following styled components.

```javascript
export const BottomStyling = styled.View`
  height: 40%;
  align-items: center;
  justify-content: center;
`;

export const ButtonStyled = styled.Text`
  font-size: 20;
  color: #fff;
`;
```

11. Import and render them in `Home.js` under the closing tag of `TopStyling`

```javascript
 <TopStyling>
   <Title>Cookies & Beyond</Title>
 </TopStyling>
 <BottomStyling>
   <ButtonStyled>Click here to skip</ButtonStyled>
 </BottomStyling>
```

11. Let's give it an alert for now when we click on it.

    ```javascript
    <ButtonStyled onClick={() => alert("Take me to the list of bakeries")}>
      Click here to skip
    </ButtonStyled>
    ```

    Let's try it out. Oops, nothing happened. That's because in a phone application we don't **click** on the screen, we **press** it.

12. Change `onClick` to `onPress`.

    ```javascript
    <ButtonStyled onPress={() => alert("Take me to the list of bakeries")}>
      Click here to skip
    </ButtonStyled>
    ```

    It's working!!
