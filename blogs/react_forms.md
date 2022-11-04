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
And rest assured, I won't be going through any CSS here. Once we get rid of all the boilerplate, let's think of the input fields that scare us. Radio buttons? Textarea? Date? Checkboxes? Think about anything. All I can promise you is that I can make react forms much easier than you thought. Unfortunately, this method won't work for input files, tho :(.

In the old times of HTML, the `FormData` object was the trend with form. Just pass `event.currentTarget` as a parameter on the object, and we can access any input we like by doing `FormData(event.currentTarget).get(name)`. Before I explain much, lets look at the code.

<iframe src="https://codesandbox.io/p/github/satvik-1203/React-Form/draft/spring-resonance?file=%2Fsrc%2FApp.tsx" title="code"></iframe>
