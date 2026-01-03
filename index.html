<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PRO-CODER AI | Expert Developer Assistant</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/themes/prism-tomorrow.min.css" rel="stylesheet" />
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600&family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-dark: #0a0a0b;
            --accent-green: #10b981;
            --terminal-gray: #1e1e20;
        }

        body {
            background-color: var(--bg-dark);
            color: #e5e7eb;
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
        }

        .code-font {
            font-family: 'Fira Code', monospace;
        }

        .glass-panel {
            background: rgba(30, 30, 32, 0.7);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .custom-scrollbar::-webkit-scrollbar {
            width: 4px;
        }

        .custom-scrollbar::-webkit-scrollbar-track {
            background: transparent;
        }

        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #333;
            border-radius: 10px;
        }

        .glow-button:hover {
            box-shadow: 0 0 15px rgba(16, 185, 129, 0.4);
        }

        pre[class*="language-"] {
            border-radius: 8px;
            margin: 1rem 0;
            background: #121214 !important;
            border: 1px solid #2d2d2d;
        }

        .typing-dot {
            width: 6px;
            height: 6px;
            background: var(--accent-green);
            border-radius: 50%;
            animation: bounce 1.4s infinite ease-in-out both;
        }

        .typing-dot:nth-child(1) { animation-delay: -0.32s; }
        .typing-dot:nth-child(2) { animation-delay: -0.16s; }

        @keyframes bounce {
            0%, 80%, 100% { transform: scale(0); }
            40% { transform: scale(1); }
        }

        .message-in {
            animation: slideIn 0.3s ease-out;
        }

        @keyframes slideIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body class="h-screen flex flex-col">

    <!-- Header -->
    <header class="glass-panel border-b border-white/10 p-4 flex items-center justify-between sticky top-0 z-50">
        <div class="flex items-center gap-3">
            <div class="w-10 h-10 bg-emerald-600 rounded-lg flex items-center justify-center shadow-lg shadow-emerald-900/20">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4" />
                </svg>
            </div>
            <div>
                <h1 class="text-xl font-bold tracking-tight text-white">PRO-CODER <span class="text-emerald-500 text-sm font-mono uppercase tracking-widest ml-1">v2.5</span></h1>
                <p class="text-[10px] text-gray-500 font-mono flex items-center gap-1">
                    <span class="w-2 h-2 bg-emerald-500 rounded-full animate-pulse"></span> SYSTEM ONLINE
                </p>
            </div>
        </div>
        <div class="flex gap-4">
            <button onclick="clearChat()" class="text-gray-400 hover:text-white transition-colors">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16" />
                </svg>
            </button>
        </div>
    </header>

    <!-- Chat Area -->
    <main id="chat-container" class="flex-1 overflow-y-auto p-4 md:p-8 space-y-6 custom-scrollbar bg-[radial-gradient(circle_at_50%_50%,_#111_0%,_#0a0a0b_100%)]">
        <!-- Welcome Message -->
        <div class="max-w-3xl mx-auto space-y-4">
            <div class="bg-terminal-gray/40 border border-white/5 p-6 rounded-2xl text-center">
                <h2 class="text-2xl font-semibold mb-2">Selamat Datang, Programmer.</h2>
                <p class="text-gray-400 text-sm">Saya adalah asisten AI pro yang dioptimalkan untuk logika, coding, dan pemecahan masalah kompleks.</p>
                <div class="grid grid-cols-2 gap-2 mt-6">
                    <button onclick="setPrompt('Optimalkan fungsi Python ini untuk kecepatan...')" class="text-xs bg-white/5 border border-white/10 p-2 rounded hover:bg-white/10 text-left">⚡ Optimize Logic</button>
                    <button onclick="setPrompt('Jelaskan konsep arsitektur Microservices secara detail')" class="text-xs bg-white/5 border border-white/10 p-2 rounded hover:bg-white/10 text-left">🏗️ Architecture Design</button>
                </div>
            </div>
        </div>
    </main>

    <!-- Typing Indicator -->
    <div id="typing-indicator" class="hidden max-w-3xl mx-auto px-4 py-2">
        <div class="flex items-center gap-2 text-emerald-500 font-mono text-xs">
            <div class="flex gap-1">
                <div class="typing-dot"></div>
                <div class="typing-dot"></div>
                <div class="typing-dot"></div>
            </div>
            <span>ANALYZING CODE...</span>
        </div>
    </div>

    <!-- Input Bar -->
    <div class="p-4 md:p-8 pt-0">
        <div class="max-w-4xl mx-auto relative group">
            <div class="absolute -top-12 left-0 w-full flex justify-center hidden" id="error-box">
                <div class="bg-red-500/20 text-red-400 border border-red-500/50 px-4 py-1 rounded-full text-xs" id="error-message"></div>
            </div>
            
            <div class="glass-panel rounded-2xl p-2 shadow-2xl flex items-end gap-2 border-white/10 group-focus-within:border-emerald-500/50 transition-all duration-300">
                <textarea 
                    id="user-input"
                    rows="1"
                    placeholder="Tanyakan kode atau logika..."
                    class="flex-1 bg-transparent border-none focus:ring-0 text-white p-3 resize-none max-h-60 custom-scrollbar code-font text-sm"
                    oninput="this.style.height = ''; this.style.height = this.scrollHeight + 'px'"
                ></textarea>
                <button 
                    onclick="handleSubmit()"
                    class="bg-emerald-600 hover:bg-emerald-500 text-white p-3 rounded-xl transition-all glow-button shrink-0"
                >
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                        <path d="M10.894 2.553a1 1 0 00-1.788 0l-7 14a1 1 0 001.169 1.409l5-1.429A1 1 0 009 15.571V11a1 1 0 112 0v4.571a1 1 0 00.725.962l5 1.428a1 1 0 001.17-1.408l-7-14z" />
                    </svg>
                </button>
            </div>
            <p class="text-center text-[10px] text-gray-600 mt-3 font-mono tracking-widest">POWERED BY GEMINI 2.5 FLASH PRO | NEURAL ENGINE</p>
        </div>
    </div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/prism.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/components/prism-python.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/components/prism-javascript.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/marked/4.3.0/marked.min.js"></script>

    <script>
        const apiKey = "AIzaSyCpjvAEDXvNu4auskVCME5cXizimgkldNg";
        const chatContainer = document.getElementById('chat-container');
        const userInput = document.getElementById('user-input');
        const typingIndicator = document.getElementById('typing-indicator');
        const errorBox = document.getElementById('error-box');
        const errorMessage = document.getElementById('error-message');

        // Configure Marked.js for code blocks
        marked.setOptions({
            highlight: function(code, lang) {
                if (Prism.languages[lang]) {
                    return Prism.highlight(code, Prism.languages[lang], lang);
                }
                return code;
            },
            breaks: true
        });

        async function fetchGemini(prompt, retries = 5, delay = 1000) {
            const url = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;
            
            const payload = {
                contents: [{ parts: [{ text: prompt }] }],
                systemInstruction: { 
                    parts: [{ text: "Anda adalah PRO-CODER AI, asisten pemrograman tingkat lanjut. Gunakan nada bicara profesional, teknis, namun ramah. Jika ada kode, formatlah dengan markdown yang tepat. Anda memiliki pengetahuan mendalam tentang semua bahasa pemrograman." }] 
                }
            };

            try {
                const response = await fetch(url, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                if (!response.ok) {
                    if (response.status === 429 && retries > 0) {
                        await new Promise(res => setTimeout(res, delay));
                        return fetchGemini(prompt, retries - 1, delay * 2);
                    }
                    throw new Error(`API Error: ${response.status}`);
                }

                const result = await response.json();
                return result.candidates?.[0]?.content?.parts?.[0]?.text || "Maaf, sistem sedang sibuk.";
            } catch (error) {
                if (retries > 0) {
                    await new Promise(res => setTimeout(res, delay));
                    return fetchGemini(prompt, retries - 1, delay * 2);
                }
                throw error;
            }
        }

        function addMessage(text, isUser = false) {
            const wrapper = document.createElement('div');
            wrapper.className = `flex ${isUser ? 'justify-end' : 'justify-start'} message-in`;
            
            const content = isUser 
                ? `<div class="bg-emerald-600 text-white px-4 py-2 rounded-2xl rounded-tr-none max-w-[85%] text-sm shadow-lg shadow-emerald-900/10">${text}</div>`
                : `<div class="max-w-[90%] md:max-w-3xl space-y-2">
                    <div class="flex items-center gap-2 mb-1">
                        <div class="w-6 h-6 bg-terminal-gray border border-white/10 rounded flex items-center justify-center text-[10px] text-emerald-500 font-bold">PC</div>
                        <span class="text-[10px] font-mono text-gray-500 uppercase tracking-tighter">AI Assistant</span>
                    </div>
                    <div class="glass-panel text-gray-200 px-5 py-4 rounded-2xl rounded-tl-none text-sm prose prose-invert prose-emerald max-w-none">
                        ${marked.parse(text)}
                    </div>
                    <button onclick="copyToClipboard(this)" class="text-[10px] text-gray-600 hover:text-emerald-500 flex items-center gap-1 transition-colors">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-3 w-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7v8a2 2 0 002 2h6a2 2 0 002-2V7a2 2 0 00-2-2h-6a2 2 0 00-2 2z" />
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 5a2 2 0 012-2h2a2 2 0 012 2m0 0h2a2 2 0 012 2v3m2 4H10" />
                        </svg>
                        Copy Response
                    </button>
                   </div>`;
            
            wrapper.innerHTML = content;
            chatContainer.appendChild(wrapper);
            chatContainer.scrollTo({ top: chatContainer.scrollHeight, behavior: 'smooth' });
            
            // Re-highlight any code blocks
            Prism.highlightAll();
        }

        async function handleSubmit() {
            const text = userInput.value.trim();
            if (!text) return;

            userInput.value = '';
            userInput.style.height = 'auto';
            errorBox.classList.add('hidden');

            addMessage(text, true);
            typingIndicator.classList.remove('hidden');
            chatContainer.scrollTo({ top: chatContainer.scrollHeight, behavior: 'smooth' });

            try {
                const response = await fetchGemini(text);
                addMessage(response, false);
            } catch (error) {
                errorMessage.innerText = "Koneksi gagal. Silakan coba lagi nanti.";
                errorBox.classList.remove('hidden');
            } finally {
                typingIndicator.classList.add('hidden');
            }
        }

        function setPrompt(text) {
            userInput.value = text;
            userInput.focus();
            userInput.dispatchEvent(new Event('input'));
        }

        function clearChat() {
            chatContainer.innerHTML = '';
            addMessage("History dibersihkan. Sesi baru dimulai.", false);
        }

        function copyToClipboard(btn) {
            const text = btn.previousElementSibling.innerText;
            const el = document.createElement('textarea');
            el.value = text;
            document.body.appendChild(el);
            el.select();
            document.execCommand('copy');
            document.body.removeChild(el);
            
            const originalText = btn.innerHTML;
            btn.innerHTML = '<span>Copied!</span>';
            setTimeout(() => btn.innerHTML = originalText, 2000);
        }

        // Handle Enter key
        userInput.addEventListener('keydown', (e) => {
            if (e.key === 'Enter' && !e.shiftKey) {
                e.preventDefault();
                handleSubmit();
            }
        });
    </script>
</body>
</html>
