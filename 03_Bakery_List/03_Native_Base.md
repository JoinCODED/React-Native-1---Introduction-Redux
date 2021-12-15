The styling is horrible! We need to fix the styling for our list to show. This sounds very exhausting. We need some bootstrap magic. But there's no Bootstrap in React Native, but there is something cooler called [Native Base](https://nativebase.io/).

1. Install `native-base`.

   ```shell
   $ npm install native-base
   ```

2. Import `NativeBaseProvider` from 'native-base':

```javascript
import { NativeBaseProvider } from 'native-base';
```

3. Wrap your main component in `app.js` with `NativeBaseProvider`.

```javascript
<NativeBaseProvider>
  <View style={styles.container}>
    {/* <Home /> */}
    <BakeryList />
    <StatusBar style="auto" />
  </View>
</NativeBaseProvider>
```

4. In `BakeryList`, import `VStack` from `native-base`.

   ```javascript
   import { VStack } from 'native-base';
   ```

5. Wrap `bakeryList` with `List` instead of `View`.

   ```javascript
   return <VStack space="5">{bakeryList}</VStack>;
   ```

6. Now let's style `BakeryItem`. Import `HStack` from `native-base` and wrap `Text` with it. add the bakery image by importing `Image` from `native-base` Amazing right?!

   ```javascript
   <HStack w="100%" alignItems="center" space="3">
     <Text>{bakery.name}</Text>
   </HStack>
   ```

7. Let's also display the image of each shop using native-base's `Image` component.

   ```javascript
   import { HStack, Image } from 'native-base';
   const BakeryItem = ({ bakery }) => {
     return (
       <HStack w="100%" alignItems="center" space="3">
         <Image
           source={{
             uri: bakery.image,
           }}
           alt="image"
           style={{ width: 100, height: 100 }}
         />
         <Text>{bakery.name}</Text>
       </HStack>
     );
   };
   ```

8. Another cool component from Native Base is the `Spinner`. Import it in `BakeryList` and render it instead of `Loading...`.

   ```javascript
   if (loading) return <Spinner />;
   ```
