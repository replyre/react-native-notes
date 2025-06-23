

## 📝 React Native `TextInput` 

---

### 🧠 **What is `TextInput`?**

`TextInput` is a core React Native component used for user **text input** (like forms, search bars, login fields).

---

### 🧱 **Basic Syntax**

```jsx
import { TextInput } from 'react-native';

<TextInput
  placeholder="Enter something..."
  onChangeText={(text) => setText(text)}
  value={text}
/>
```

---

### ⚙️ **Common Props**

| Prop              | Type      | Description                                                         |
| ----------------- | --------- | ------------------------------------------------------------------- |
| `value`           | `string`  | The current text input value                                        |
| `onChangeText`    | `func`    | Callback when the text changes                                      |
| `placeholder`     | `string`  | Hint text when input is empty                                       |
| `secureTextEntry` | `boolean` | For password fields (`true` hides characters)                       |
| `keyboardType`    | `string`  | Type of keyboard: `'default'`, `'numeric'`, `'email-address'`, etc. |
| `multiline`       | `boolean` | Allows multiple lines of input                                      |
| `maxLength`       | `number`  | Limits the number of characters                                     |
| `editable`        | `boolean` | Enables/disables editing                                            |
| `autoFocus`       | `boolean` | Automatically focuses input on mount                                |
| `style`           | `object`  | Styling for the input box                                           |

---

### ✨ **Examples**

#### ✅ **Basic Input with State**

```jsx
const [text, setText] = useState('');

<TextInput
  placeholder="Type here..."
  value={text}
  onChangeText={setText}
/>
```

---

#### 🔐 **Password Input**

```jsx
<TextInput
  secureTextEntry={true}
  placeholder="Enter Password"
/>
```

---

#### 🧮 **Number Keyboard**

```jsx
<TextInput
  keyboardType="numeric"
  placeholder="Enter Age"
/>
```

---

#### 📝 **Multi-line Input**

```jsx
<TextInput
  multiline={true}
  numberOfLines={4}
  placeholder="Write your message..."
  style={{ height: 100, textAlignVertical: 'top' }}
/>
```

---

### 🎨 **Styling Tip**

```jsx
const styles = StyleSheet.create({
  input: {
    borderWidth: 1,
    borderColor: '#ccc',
    padding: 10,
    borderRadius: 5,
    marginVertical: 10,
  },
});

<TextInput style={styles.input} />
```

---

### 🚨 **Do's and Don'ts**

| ✅ Do                                     | ❌ Don’t                          |
| ---------------------------------------- | -------------------------------- |
| Bind value to state with `useState()`    | Use uncontrolled inputs          |
| Use `onChangeText` instead of `onChange` | Expect HTML-like behavior        |
| Use styles to control size/padding       | Use `height: 'auto'` (not valid) |

---

### 📌 **Where It’s Used**

* Login / Signup forms
* Search bars
* Feedback / chat apps
* Any input field in a form

