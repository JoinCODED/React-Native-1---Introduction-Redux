Now when we navigate to a bakery, we should only see its cookies. If you check the list of bakeries, you'll see that every bakery has a list of cookie IDs.

What we need to do is pass the bakery object to `CookieList`.

1. In `BakeryItem` we will pass `navigate` another argument which is an object, the key is the name of your route param and the value is whatever you want to pass.

    ```javascript
    <ListItem
      onPress={() =>
        navigation.navigate("Cookies", { bakery: bakery })
      }
    >
      <BakeryItemStyled>{bakery.name}</BakeryItemStyled>
    </ListItem>
    ```


   How can we receive it in `CookieList`? Let's check `props` again in RN Debugger, you'll see that its saved in `route.params`.

2. So we will destruct `props` and receive `route`, then from `route` we will take the value of `bakery`.

    ```javascript
    const CookieList = ({ navigation, route }) => {
      if (cookieStore.loading) return <Spinner />;
      const { bakery } = route.params;
    ```

3. Now, we will `map` over `bakery.cookies` and pass every `cookie` to `cookieStore.fetchCookie` which will `find` the cookie by its ID in the `cookieStore` and return it. Then we will map over the returned array and pass it to `CookieItem`.

    ```javascript
    const cookieList = bakery.cookies
    .map((cookie) => cookieStore.getCookieById(cookie.id))
    .map((cookie) => <CookieItem cookie={cookie} key={cookie.id} />);
    ```

4. Let's check our app again. Yes! It works!