# Indentation With Tab Key In React

Hello World!

The "Tabulator key" commonly known as the "Tab" key has multiple purposes, depending on where it is being used. For example, if we hit the tab key in a spreadsheet, it would move the cursor one cell rightwards. If we hit it in a text editor or word processor, it would indent the cursor horizontally rightwards. If we hit tab in a form, it would move to the next form element. If we hit it on a random website, it would move to the next accessible element on the page (like a button or a text field). Likewise, the functionality of the tab key varies from place to place. In this article, let's see how we can override the tab functionality in a react form's text area.

## Scenario

![Photo by Alvaro Reyes on Unsplash](https://cdn.hashnode.com/res/hashnode/image/upload/v1671892343420/671cb9b5-c482-43ea-8222-c233385e64c5.jpeg align="center")

Let's consider we have a form in a react app, which contains fields to get input from users. We have a scenario, where we need to write a python code inside a text area component. We know that indentation is very important in python and a wrong indentation would break the functioning of code (If you don't know why indentation is important, [check this article](https://www.geeksforgeeks.org/indentation-in-python/)). But if we hit the tab button in a text area, instead of adding horizontal indentation, it would move to the next accessible element on the page. To overcome this, we will have to override the functionality of the tab key.

## Implementation

![Photo by Chris Ried on Unsplash ](https://cdn.hashnode.com/res/hashnode/image/upload/v1671892726762/76bb84a9-44df-471b-88c6-20f937aedeb7.jpeg align="center")

### Actual behaviour

Let us create a normal text area component in a react app and try to hit the tab key. Below would be the implementation:

```javascript
import React, { useState } from "react";

const NormalTextArea = () => {
  // State to store value typed in text area
  const [val, setVal] = useState("");
  return (
    <textarea value={val} onChange={(e) => setVal(e.target.value)}></textarea>
  );
};

export default NormalTextArea;
```

When we run the code and hit on the tab button, instead of adding indentation, it would move to the next accessible element on the page like this.

![Tab behaviour in normal text area.](https://cdn.hashnode.com/res/hashnode/image/upload/v1671893259708/2a665c74-ea3f-4f56-b199-8e93db1d8f6d.gif align="center")

### Override the tab functionality

To insert horizontal indentation on the tab press, we will need to override the default behaviour of the tab key. We will write a `handleTab` function and call it when `onKeyDown` event is triggered. We also need to modify the `value` state to cursor position and target element. The value state would be changed like this:

```javascript
const [value, setValue] = useState({ value: "", position: -1, target: null });
```

The `handleTab` function would be like this:

```javascript
const handleTab = (e) => {
    // Storing the content
    let content = e.target.value;
    // Storing current cursor position
    let position = e.target.selectionStart;
    // Checking if key pressed is tab
    if (e.key === "Tab") {
      // Preventing default behaviour of tab key.
      e.preventDefault();
      // Inserting horizontal indentation (4 spaces in this case) in respective cursor position
      let newText =
        content.substring(0, position) +
        " ".repeat(TAB_SPACE) +
        content.substring(position);
      // Setting value, position and target after indentation.
      setValue({
        value: newText,
        position: position + TAB_SPACE,
        target: e.target
      });
    } else {
      // if key pressed is not tab, just updating position and target.
      setValue((pr) => ({
        ...pr,
        position,
        target: e.target
      }));
    }
  }
```

Since the structure of `value` is changed, we will have to write a function to store value when the text area value is changed. The function would be like this:

```javascript
const handleKeyChange = (e) => {
    setValue({
      value: e.target.value,
      position: e.target.selectionStart,
      target: e.target
    });
  };
```

Now, whenever the `val` is changed, we will have to change the position of the cursor accordingly. For that, we can create a ref for the text area and set the `selectionStart` with `value.position`. We can do this in an `useEffect` like this:

```javascript
useEffect(() => {
    textRef.current.selectionStart = value.position;
  }, [value]);
```

The text area component would be like this:

```xml
<textarea
    ref={textRef}
    onKeyDown={handleTab}
    value={value.value}
    onChange={handleKeyChange}
></textarea>
```

Now we will be able to add indentation on the tab click.

![Post overriding the tab key](https://cdn.hashnode.com/res/hashnode/image/upload/v1671895815750/bb5e0022-8a1c-4fdc-a60e-5a2f75791731.png align="center")

The final code would be:

```javascript
import React, { useRef, useState, useEffect } from "react";

const TabTextArea = () => {
  const TAB_SPACE = 4;
  // Storing value, position and element in state
  const [value, setValue] = useState({ value: "", position: -1, target: null });
  // Track the value change and updating the cursor position
  useEffect(() => {
    textRef.current.selectionStart = value.position;
  }, [value]);
  // Function triggered when text area values changed
  const handleKeyChange = (e) => {
    setValue({
      value: e.target.value,
      position: e.target.selectionStart,
      target: e.target
    });
  };
  // Function to handle tab key press
  const handleTab = (e) => {
    let content = e.target.value;
    let position = e.target.selectionStart;
    if (e.key === "Tab") {
      e.preventDefault();
      let newText =
        content.substring(0, position) +
        " ".repeat(TAB_SPACE) +
        content.substring(position);
      setValue({
        value: newText,
        position: position + TAB_SPACE,
        target: e.target
      });
    } else {
      setValue((pr) => ({
        ...pr,
        position,
        target: e.target
      }));
    }
  };
  // Ref created for text area
  const textRef = useRef();
  return (
    <textarea
      ref={textRef}
      onKeyDown={handleTab}
      value={value.value}
      onChange={handleKeyChange}
    ></textarea>
  );
};

export default TabTextArea;
```

Here is the implementation of the code:

%[https://codesandbox.io/embed/tab-indentation-bgdlyb?fontsize=14&hidenavigation=1&theme=dark&view=preview] 

Hope this is useful to you. Looking forward to your feedback and suggestions. Thank you!