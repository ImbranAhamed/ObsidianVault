Aha, you want to _peek under the hood_—not the finished JSON, but the actual raw byte stream itself. Perfectly legitimate curiosity.

Here’s a little snippet that will let you log each chunk of bytes as they arrive from the `ReadableStream`:

```js
const response = await fetch("https://jsonplaceholder.typicode.com/users");
const reader = response.body.getReader();

while (true) {
  const { done, value } = await reader.read();
  if (done) break;

  console.log(value); // Uint8Array of raw bytes
}
```

Each `value` there is a `Uint8Array`, meaning it’s a typed array of raw bytes — little numbers between 0 and 255. That’s what the browser actually gets over the network before turning it into text or JSON.

If you want to _see_ the text content of those bytes as they stream in, you can decode them with a `TextDecoder`:

```js
const decoder = new TextDecoder();
const response = await fetch("https://jsonplaceholder.typicode.com/users");
const reader = response.body.getReader();

while (true) {
  const { done, value } = await reader.read();
  if (done) break;

  console.log(decoder.decode(value, { stream: true }));
}
```

That version prints out the text chunks in real time as they’re downloaded.

The fun bit: those byte arrays are what allow streams to be processed before the full file finishes downloading — it’s how browsers stream video, parse large JSON files, or even progressively render HTML. It’s a small window into the bloodstream of the web.