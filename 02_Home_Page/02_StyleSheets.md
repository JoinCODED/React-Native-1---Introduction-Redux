But will we keep using inline styling? Can we create a stylesheet for our React Native components? Yes we can!

1. In `Home.js` outside the component create a constant named `styles` and assign it to `StyleSheet.create`, don't forget to import `StyleSheet` from react-native .

   ```javascript
   import { StyleSheet, Text, View } from 'react-native';
   ```

const styles = StyleSheet.create({});

2. Let's create a styles for our `ImageBackground`, `View` and `Text` and move our styling.

```javascript
const styles = StyleSheet.create({
  homeBackground: {
    flex: 1,
    width: '100%',
    height: '100%',
  },
  view: {
    height: '40%',
    alignItems: 'center',
    justifyContent: 'center',
  },
  title: {
    color: '#000',
    fontSize: 38,
    textAlign: 'center',
  },
});
```

3. Let's use them in `Home.js`.

   ```javascript
   return (
    <ImageBackground
      style={styles.homeBackground}
      source={{
        uri: 'https://annabanana.co/wp-content/uploads/2020/03/Chocolate-Chip-Cookies-22.jpg',
      }}
    >
      <View style={styles.view}>
        <Text style={styles.title}>Cookies & Beyond</Text>
      </View>
    </ImageBackground>
   ```

4. Let's add a button that we can click on later to take us to the list of shops. In `styles`, create the following styles.

```javascript
  button: {
    fontSize: 20,
    color: '#fff'
  }
```

11.Import `Button` from react-native then render the button in `Home.js` under the `Text` tag.

```javascript
<ImageBackground
  style={styles.homeBackground}
  source={{
    uri: 'https://annabanana.co/wp-content/uploads/2020/03/Chocolate-Chip-Cookies-22.jpg',
  }}
>
  <View style={styles.view}>
    <Text style={styles.title}>Cookies & Beyond</Text>
    <Button style={styles.button} title="Click" />
  </View>
</ImageBackground>
```

11. Let's give it an alert for now when we click on it.

    ```javascript
    <Button
      onClick={() => alert('Take me to the list of shops')}
      style={styles.button}
      title="Click"
    />
    ```

    Let's try it out. Oops, nothing happened. That's because in a phone application we don't **click** on the screen, we **press** it.

12. Change `onClick` to `onPress`.

    ```javascript
    <Button
      onPress={() => alert('Take me to the list of shops')}
      style={styles.button}
      title="Click"
    />
    ```

    It's working!!
