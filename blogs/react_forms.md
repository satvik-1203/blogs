---
name: React Forms
Topics: JavaScript, React
Date: 11/03/2022
---

# React Forms

```txt:terminal showLineNumbers
yarn create vite
```

Following Questions:

- name of the repo
- Framework: React
- I'll be going with TypeScript

Once you finished the steps, you should have a repo with what ever you named.

```txt:terminal showLineNumbers
cd react-forms
yarn install
```

We all know forms and React. Eww, they don't go well. After Remix came out, for new developers like me who started with the modern web, forms surprised me with how easy it used to be in the old times and how complicated the React community made it by using state management, onChange functions, etc. Primarily working with radio buttons, dates, and other input fields scared me. And the one thing I always hated about forms and using state is making it rerender on every change in the input box. Is it required? I know it's a cheap process, but it makes me shiver. I came up with another solution. However, it's not the ideal way. But cleaner than the traditional way of creating forms. So, let's get it.

For starters, before we dive in, remove all the boilerplate that comes with it.
And rest assured, I won't be going through any CSS here. Once we get rid of all the boilerplate, let's think of the input fields that scare us. Radio buttons? Textarea? Date? Checkboxes? Think about anything. All I can promise is that I can make react forms much easier than you thought. Unfortunately, this method won't work for input files, tho :(.

In the old times of HTML, the `FormData` object was the trend with form. Just pass `event.currentTarget` as a parameter on the object, and we can access any input we like by doing **FormData(event.currentTarget).get(<input name>)**. Before I explain much, let's look at the code. Just fill in all the fields in the form and once you click submit, look how we get all the data with no use of state, onChange functions, or whatsoever.

<iframe src="https://codesandbox.io/embed/github/satvik-1203/React-Form?module=/src/App.tsx&fontsize=12&view=split" title="code" height="800"></iframe>

The code structure uses labels and an input tag; the label tag is optional. However, what is required is the `name` attribute on the input tag, which is the key when we get them into the object. We can then have our general onSubmit function that prevents default and get all the values from the input fields. After making the FormObject, we can send it to a server using fetch or whatever you want.

```js:App.tsx/onSubmit showLineNumbers

  const onSubmit = (e: React.FormEvent<HTMLFormElement>) => {
    e.preventDefault();
    const formData = new FormData(e.currentTarget);

    const formDataObj: { [key: string]: string } = {};

    // Iterate through every key in form data and put it in the object

    formData.forEach((value, key) => {
      formDataObj[key] = value as string;
    });

    // Stored the data in state so I can represent it on window

    setFormDataState(formDataObj);
  };

```

```html:App.tsx showLineNumbers

<label>Full Name</label>

<!-- Name stands for key in the object -->

<input type="text" name="fullname" />

```

You could argue if you want the data on another event which isn't form event, in those scenarios, we could use `useRef.` I said useRef since it lets us access the form event anywhere in the code just by doing **ref.current**.

And its really just that easy.
