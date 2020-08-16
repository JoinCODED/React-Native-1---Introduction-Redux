In VSCode, open `App.js` which is the application's starting point. Note that we're not using JSX tags, we're importing and rendering pre-built components from `react-native`.

Take a look at the [documentation](https://reactnative.dev/docs/components-and-apis#basic-components) to learn more about the basic components.

Let's create our `Home` component and try out some of those components.

1. Create a new folder called `components`.

2. Create a folder inside `components` called `Home`, inside it create an `index.js` file and setup up your component.

3. Let's start with the `ImageBackground` component. Import it from `react-native` and render it.
    
    ```javascript
    import React from "react";

    // Styling
    import { ImageBackground } from "react-native";

    const Home = () => {
        return (
            <ImageBackground></ImageBackground>
        );
    };

    export default Home;
    ```

4. `ImageBackground` requires an image `source` and `width` and `height` for styling.

    ```javascript
    <ImageBackground 
        style={{ flex: 1, width: "100%", height: "100%" }}
        source={{
            uri: "https://annabanana.co/wp-content/uploads/2020/03/Chocolate-Chip-Cookies-22.jpg",
        }}
    ></ImageBackground>
    ```

5. In the top, I want to add a title. So we'll style the half top using a `View` component from `react-native` which is similar to `div` in HTML. 

     ```javascript
    <ImageBackground 
        style={{ flex: 1, width: "100%", height: "100%" }}
        source={{
            uri: "https://annabanana.co/wp-content/uploads/2020/03/Chocolate-Chip-Cookies-22.jpg",
        }}
    >
        <View style={{ height: "40%", alignItems: "center", justifyContent: "center"}}></View>
    </ImageBackground>
    ```   

6. Inside it I'll add a `Text` component from `react-native` and style it a bit.

     ```javascript
    <ImageBackground 
        style={{ flex: 1, width: "100%", height: "100%" }}
        source={{
            uri: "https://annabanana.co/wp-content/uploads/2020/03/Chocolate-Chip-Cookies-22.jpg",
        }}
    >
        <View style={{ height: "40%", alignItems: "center", justifyContent: "center"}}>
            <Text style={{ color: "#fff", fontSize: 38,textAlign: "center"}}>
                Cookies & Beyond
            </Text>
        </View>
    </ImageBackground>
    ```


