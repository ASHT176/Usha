<!DOCTYPE html>
<html>
<head>
  <title>My Free AI Chatbot</title>
  <style>
    body { font-family: Arial; background: #f4f4f4; }
    #chatbox { width: 400px; margin: 20px auto; padding: 10px; background: #fff; border-radius: 8px; }
    .msg { margin: 10px 0; }
    .user { color: blue; }
    .bot { color: green; }
  </style>
</head>
<body>
  <div id="chatbox">
    <div id="messages"></div>
    <input id="input" type="text" placeholder="Type a message..." />
    <button onclick="sendMessage()">Send</button>
  </div>

  <script>
    async function sendMessage() {
      const input = document.getElementById("input");
      const msg = input.value;
      document.getElementById("messages").innerHTML += `<div class="msg user">You: ${msg}</div>`;
      input.value = "";
      const res = await fetch(`https://your-backend-url/chat?msg=${msg}`);
      const data = await res.json();
      document.getElementById("messages").innerHTML += `<div class="msg bot">Bot: ${data.reply}</div>`;
    }
  </script>
</body>
</html>

