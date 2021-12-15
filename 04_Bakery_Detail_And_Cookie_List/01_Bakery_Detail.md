Let's create a bakery detail page.

1. In your `components/` folder, create `BakeryDetail.js` and setup your component.

2. In Bakery Detail, we'll start by displaying the shop's name and image. Create these styles in your StyleSheet for the detail page:

```javascript
const styles = StyleSheet.create({
  BakeryDetailWrapper: {
    marginTop: 50,
  },
  BakeryDetailImage: {
    width: 150,
    height: 150,
  },
  BakeryDetailTitle: {
    fontWeight: 'bold',
    fontSize: 40,
  },
});
```

3. Render them in your detail component. For now, display only the first bakery in your bakeryStore.

   ```javascript
   const BakeryDetail = () => {
     const bakery = useSelector((state) => state.bakeryReducer.bakeries[0]);
     return (
       <View style={styles.shopDetailWrapper}>
         <Image style={styles.shopDetailImage} source={{ uri: bakery.image }} />
         <Text style={styles.shopDetailTitle}>{bakery.name}</Text>
       </View>
     );
   };

   export default BakeryDetail;
   ```

4. In your `App`, comment the `BakeryList` and render `BakeryDetail` instead.

5. Oops! It's breaking.. This is because the store is still requesting the bakeries from the backend, so we need to make our detail component into an observer and put an if-statement.

   ```javascript
   const BakeryDetail = () => {
     const loading = useSelector((state) => state.bakeryReducer.loading);
     const bakery = useSelector((state) => state.bakeryReducer.bakeries[0]);
     if (loading) return <Spinner />;
     return (
       <View style={styles.BakeryDetailWrapper}>
         <Image
           style={styles.BakeryDetailImage}
           source={{ uri: bakery.image }}
         />
         <Text style={styles.BakeryDetailTitle}>{bakery.name}</Text>
       </View>
     );
   };

   export default BakeryDetail;
   ```
