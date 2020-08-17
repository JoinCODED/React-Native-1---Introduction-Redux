1. Install `react-navigation/native`.

    ```bash
    $ yarn add @react-navigation/native
    ```

2. Import `createStackNavigator` from 

    ```javascript
    import { createStackNavigator } from "@react-navigation/stack";
    ```

3. Now we'll call `createStackNavigator` **outside** the `App` component, and save it in a variable called `Stack`. Let's console log it to see what's inside it.
   
    ```javascript
    const Stack = createStackNavigator();
    console.log("App -> Stack", Stack);
    ```

    `createStackNavigator` returns an object that has two properties, `Navigator` and `Screen`. Both `Navigator` and `Screen` are components.

4. Let's de-structure Stack.

    ```javascript
    const { Navigator, Screen } = createStackNavigator();

    export default function App() {
        ...
    }
    ```

5. Wrap `Home` with `Navigator`. 

    ```javascript
    export default function App() {
      return (
        <NavigationContainer>
          <Navigator>
            <Home />
          </Navigator>
        </NavigationContainer>
      );
    }
    ```

    This will give us an error. We can't render components directly inside a `Navigator` component.

6. To define a component as a screen, we will render `Screen` and pass the component as a `prop`. Every `Screen` must be given a name as well.

    ```javascript
    export default function App() {
      return (
        <NavigationContainer>
          <Navigator>
            <Screen name="Home" component={Home} />
          </Navigator>
        </NavigationContainer>
      );
    }
    ```

    Let's take a look. Yes! It's working! And what's this? We got a header without asking for one! How cool is that?

7. Let's add more screens. 

    ```javascript
    export default function App() {
      return (
        <NavigationContainer>
          <Navigator>
            <Screen name="Home" component={Home} />
            <Screen name="Bakeries" component={BakeryList} />
          <Screen name="Cookies" component={CookieList} />
          </Navigator>
        </NavigationContainer>
      );
    }
    ```

8. How can we choose which screen appears first? We will pass `Navigator` a `prop` called `initialRouteName` and pass it the `name` of the screen we want to be first. 

    ```javascript
        <NavigationContainer>
          <Navigator initialRouteName="Home">
    ```