

## 📘 React Native: `FlatList` – Study Notes

---

### 🔍 What is `FlatList`?

`FlatList` is a performant component in React Native used for **rendering long lists of data**. Unlike `ScrollView`, `FlatList` **only renders items currently visible on the screen**, which makes it suitable for large data sets.

---

### 🧱 Basic Structure

```jsx
<FlatList
  data={dataArray}
  renderItem={({ item }) => (
    // Your JSX to render each item
  )}
  keyExtractor={item => item.id}
/>
```

---

### ⚙️ Props Explained (based on your screenshot)

| Prop                     | Description                                                                      |
| ------------------------ | -------------------------------------------------------------------------------- |
| `data`                   | The array of data you want to display (`dummy` in your case).                    |
| `renderItem`             | Function that returns JSX for each item.                                         |
| `keyExtractor`           | Function that provides a unique key for each item (`item.id`).                   |
| `ItemSeparatorComponent` | Optional component between each item (like spacing).                             |
| `numColumns`             | Number of columns to show (2 for grid layout).                                   |
| `columnWrapperStyle`     | Custom style for each row when using multiple columns (like spacing with `gap`). |

---

### ✅ Example (from your screenshot)

```jsx
<FlatList
  data={dummy}
  renderItem={({ item }) => (
    <View style={styles.card}>
      <Image source={{ uri: item.image }} style={styles.image} />
      <Text>{item.name}</Text>
      <Text>{item.email}</Text>
    </View>
  )}
  keyExtractor={item => item.id}
  ItemSeparatorComponent={() => <View style={{ height: 10 }} />}
  numColumns={2}
  columnWrapperStyle={{ gap: 10 }}
/>
```

---

### ✨ Styling Tips

* Use `numColumns` to make a **grid** layout.
* `columnWrapperStyle` lets you apply padding/gap between columns.
* To separate items vertically, use `ItemSeparatorComponent`.

---

### 📦 When to Use `FlatList` vs `ScrollView`

| `FlatList`                        | `ScrollView`                   |
| --------------------------------- | ------------------------------ |
| Efficient for large lists         | Suitable for small content     |
| Renders only visible items        | Renders everything at once     |
| Supports lazy loading, pagination | Can lead to performance issues |

---

### 🧠 Pro Tips

* Always provide a **unique key** via `keyExtractor`.
* Avoid nesting `FlatList` inside `ScrollView`.
* For best performance: use `initialNumToRender`, `onEndReached`, and `getItemLayout` if needed.

---

### 🔁 Horizontal FlatList

```jsx
<FlatList
  horizontal
  data={dummy}
  renderItem={({ item }) => <Text>{item.name}</Text>}
/>
```
