# Python-
Python project 1
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Nova AI Assistant</title>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
}

body {
    background: #0f172a;
    color: white;
    height: 100vh;
    display: flex;
    flex-direction: column;
}

/* Header */
header {
    height: 65px;
    background: #111827;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 20px;
    border-bottom: 1px solid #263244;
}

.logo {
    font-size: 22px;
    font-weight: bold;
}

.logo span {
    color: #38bdf8;
}

.clear {
    background: #1e293b;
    color: white;
    border: none;
    padding: 9px 14px;
    border-radius: 8px;
    cursor: pointer;
}

.clear:hover {
    background: #334155;
}

/* Chat */
#chat {
    flex: 1;
    overflow-y: auto;
    padding: 20px;
    display: flex;
    flex-direction: column;
    gap: 15px;
}

.message {
    max-width: 80%;
    padding: 13px 16px;
    border-radius: 15px;
    line-height: 1.5;
    white-space: pre-wrap;
}

.user {
    align-self: flex-end;
    background: #2563eb;
    border-bottom-right-radius: 4px;
}

.ai {
    align-self: flex-start;
    background: #1e293b;
    border-bottom-left-radius: 4px;
}

/* Welcome */
.welcome {
    text-align: center;
    margin: auto;
    max-width: 500px;
}

.welcome h1 {
    font-size: 36px;
    margin-bottom: 10px;
}

.welcome p {
    color: #94a3b8;
}

/* Input area */
.input-area {
    background: #111827;
    padding: 15px;
    border-top: 1px solid #263244;
    display: flex;
    gap: 10px;
}

#userInput {
    flex: 1;
    padding: 14px;
    border-radius: 12px;
    border: 1px solid #334155;
    background: #1e293b;
    color: white;
    outline: none;
    font-size: 16px;
}

#send {
    background: #38bdf8;
    border: none;
    color: #082f49;
    font-weight: bold;
    padding: 0 20px;
    border-radius: 12px;
    cursor: pointer;
}

#send:hover {
    background: #7dd3fc;
}

/* Mobile */
@media(max-width:600px) {

    .message {
        max-width: 90%;
    }

    .welcome h1 {
        font-size: 28px;
    }

    #send {
        padding: 0 15px;
    }
}
</style>
</head>

<body>

<header>
    <div class="logo">🤖 <span>Nova</span> AI</div>
    <button class="clear" onclick="clearChat()">Clear</button>
</header>

<div id="chat">

    <div class="welcome" id="welcome">
        <h1>👋 Hello!</h1>
        <p>
            I'm Nova AI. Ask me anything and I'll try to help you.
        </p>
    </div>

</div>

<div class="input-area">

    <input
        type="text"
        id="userInput"
        placeholder="Message Nova AI..."
        autocomplete="off"
    >

    <button id="send" onclick="sendMessage()">Send</button>

</div>

<script>

const input = document.getElementById("userInput");
const chat = document.getElementById("chat");
const welcome = document.getElementById("welcome");

input.addEventListener("keydown", function(event) {

    if (event.key === "Enter") {
        sendMessage();
    }

});

function addMessage(text, type) {

    if (welcome) {
        welcome.style.display = "none";
    }

    const message = document.createElement("div");

    message.classList.add("message", type);

    message.textContent = text;

    chat.appendChild(message);

    chat.scrollTop = chat.scrollHeight;

    return message;
}

function sendMessage() {

    const text = input.value.trim();

    if (text === "") {
        return;
    }

    addMessage(text, "user");

    input.value = "";

    // Thinking message
    const thinking = addMessage("Nova is thinking...", "ai");

    setTimeout(() => {

        thinking.remove();

        const response = getAIResponse(text);

        addMessage(response, "ai");

    }, 800);
}


function getAIResponse(question) {

    const q = question.toLowerCase();

    if (q.includes("hello") ||
        q.includes("hi") ||
        q.includes("hey")) {

        return "Hello! 👋 I'm Nova AI. How can I help you today?";
    }

    if (q.includes("your name")) {

        return "My name is Nova AI 🤖.";
    }

    if (q.includes("html")) {

        return "HTML is used to create the structure of websites. CSS makes them look beautiful, and JavaScript makes them interactive.";
    }

    if (q.includes("javascript") ||
        q.includes("js")) {

        return "JavaScript is a programming language used to make websites interactive. For example, buttons, games, menus and chat systems can use JavaScript.";
    }

    if (q.includes("python")) {

        return "Python is a beginner-friendly programming language used for websites, AI, automation, data science and many other things.";
    }

    if (q.includes("who are you")) {

        return "I'm Nova AI, your virtual assistant! 🤖 I can answer questions, explain topics and help you learn.";
    }

    if (q.includes("thank")) {

        return "You're welcome! 😊";
    }

    if (q.includes("game")) {

        return "I can help you create games using HTML, CSS and JavaScript! 🎮";
    }

    return "That's an interesting question! 🤔 I'm a demo AI right now, so my knowledge is limited. You can connect me to a real AI API to get much smarter answers.";
}


function clearChat() {

    chat.innerHTML = `
        <div class="welcome" id="welcome">
            <h1>👋 Hello!</h1>
            <p>
                I'm Nova AI. Ask me anything and I'll try to help you.
            </p>
        </div>
    `;

}

</script>

</body>
</html>
