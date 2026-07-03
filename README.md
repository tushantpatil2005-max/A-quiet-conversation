Chat Bot
A minimal, single-file React chat interface powered live by the Claude API. No backend, no build step — the component calls the Anthropic API directly from the browser.
Files
chatbot.jsx — the entire app (UI + API calls) in one component.
How it works
Messages are kept in React state (useState), one array of { role, text } objects.
On send, the full conversation history is POSTed to https://api.anthropic.com/v1/messages using the claude-sonnet-4-6 model.
The model's reply is appended to the message list and rendered.
A "writing…" indicator shows while waiting on a response.
Controls
Enter — send the message
Shift + Enter — insert a line break without sending
Customizing
Personality / instructions: add a system field to the request body in the fetch call inside send().
Model: change the model value in the same request body.
Response length: adjust max_tokens.
Styling: all styles are inline in the component — colors, type, and spacing are defined at the top of each element's style object, no external CSS file.
Streaming: currently responses arrive all at once; add stream: true to the request and handle server-sent events if you want token-by-token output.