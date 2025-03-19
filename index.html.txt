<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FireGuard AI Chat</title>
    <script src="fireguard_ai.js"></script> <!-- 🔥 AI File -->
    <style>
        body { font-family: Arial, sans-serif; text-align: center; }
        #chatbox { width: 80%; height: 300px; border: 1px solid black; overflow-y: auto; margin: 10px auto; padding: 10px; }
        #userInput { width: 70%; padding: 10px; }
        #sendButton { padding: 10px; }
    </style>
</head>
<body>
    <h1>FireGuard AI Chat</h1>
    <div id="chatbox"></div>
    <input type="text" id="userInput" placeholder="Type your message...">
    <button id="sendButton" onclick="sendMessage()">Send</button>

    <script>
        function sendMessage() {
            let userInput = document.getElementById("userInput").value;
            let chatbox = document.getElementById("chatbox");

            let checkContent = fireGuard.analyzeContent(userInput);
            let checkWebsite = fireGuard.analyzeWebsite(userInput);

            if (checkContent.flagged || checkWebsite.flagged) {
                chatbox.innerHTML += `<p>${checkContent.reason || checkWebsite.reason}</p>`;
                fireGuard.learnNewInappropriateWord(userInput); // 🔥 AI learns new bypasses
            } else {
                chatbox.innerHTML += `<p>You: ${userInput}</p>`;
            }

            document.getElementById("userInput").value = "";
        }
    </script>
</body>
</html>
