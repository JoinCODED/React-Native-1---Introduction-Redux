We need to install a few dependencies to use [React Navigation](https://reactnavigation.org/docs/getting-started/).

1. Install `react-navigation/native`.

    ```bash
    $ yarn add @react-navigation/native
    ```

2. Install expo dependencies. The reason why we use `expo` instead of `yarn` is that Expo will download the version of those dependencies that are compatible with your apps.

    ```bash
    $ expo install react-native-gesture-handler react-native-reanimated react-native-screens react-native-safe-area-context @react-native-community/masked-view
    ```

3. In `App.js`, wrap your `Home` component with `NavigationContainer`, which is imported from `react-navigation`.

    ```jsx
    import { NavigationContainer } from "@react-navigation/native";

    ...

    export default function App() {
     return (
       <NavigationContainer>
         <Home />
       </NavigationContainer>
     );
    }
    ```

