Now when we navigate to a bakery, we should only see its cookies. If you check the list of bakeries, you'll see that every bakery has a list of cookie IDs.

What we need to do is pass the bakery object to `BakeryDetail`.

1. In `BakeryItem` we will pass `navigate` another argument which is an object, the key is the name of your route param and the value is whatever you want to pass.

   ```javascript
   <Pressable
     onPress={() => navigation.navigate("BakeryDetail", { bakery: bakery })}
   >
   ```

   How can we receive it in `CookieList`? Let's check `props` again in RN Debugger, you'll see that its saved in `route.params`.

2. So we will destruct `props` and receive `route`, then from `route` we will take the value of `bakery`.

   ```javascript
   const BakeryDetail = ({ navigation, route }) => {
    const { bakery } = route.params;
    [...]
   }
   ```

3. Let's check our app again. Yes! It works!
