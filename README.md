<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Hybrid Studio PRO</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&family=Fira+Code:wght@400;500&display=swap" rel="stylesheet">
    <style>
        body {
            background-color: #050505;
            color: #fafafa;
            font-family: 'Inter', sans-serif;
        }
        .glass-card {
            background: rgba(20, 20, 22, 0.8);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.08);
        }
        .custom-scrollbar::-webkit-scrollbar { width: 5px; }
        .custom-scrollbar::-webkit-scrollbar-thumb { background: #333; border-radius: 10px; }
        
        .image-result {
            animation: slideIn 0.6s cubic-bezier(0.16, 1, 0.3, 1);
            max-width: 512px;
        }
        
        @keyframes slideIn {
            from { opacity: 0; transform: translateY(20px) scale(0.98); }
            to { opacity: 1; transform: translateY(0) scale(1); }
        }

        .ai-msg {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 1.2rem;
            padding: 1rem;
            max-width: 85%;
            font-size: 0.9rem;
            line-height: 1.5;
        }

        .user-msg {
            background: #4f46e5;
            color: white;
            border-radius: 1.2rem;
            padding: 0.8rem 1.2rem;
            max-width: 85%;
            font-size: 0.9rem;
        }

        .error-msg {
            background: rgba(239, 68, 68, 0.1);
            border: 1px solid rgba(239, 68, 68, 0.2);
            color: #fca5a5;
            padding: 1rem;
            border-radius: 1rem;
            font-size: 0.85rem;
        }

        .loading-pulse {
            display: inline-block;
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background-color: #6366f1;
            animation: pulse 1s infinite ease-in-out;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(0.8); opacity: 0.5; }
            50% { transform: scale(1.2); opacity: 1; }
        }
    </style>
</head>
<body class="h-screen flex flex-col overflow-hidden">

    <!-- Header -->
    <header class="p-4 border-b border-white/5 flex justify-between items-center glass-card z-10">
        <div class="flex items-center gap-3">
            <div class="w-8 h-8 bg-indigo-600 rounded flex items-center justify-center shadow-lg shadow-indigo-500/20">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
                </svg>
            </div>
            <h1 class="text-sm font-bold tracking-widest uppercase text-indigo-400">Hybrid IQ v3.0</h1>
        </div>
        <button onclick="location.reload()" class="text-xs text-gray-500 hover:text-white transition-colors font-mono tracking-tighter">RESET SESSION</button>
    </header>

    <!-- Chat Area -->
    <main id="chat-box" class="flex-1 overflow-y-auto p-4 md:p-8 space-y-6 custom-scrollbar bg-[radial-gradient(circle_at_top,_#111_0%,_#050505_100%)]">
        <div class="max-w-3xl mx-auto text-center py-20 opacity-40">
            <div class="mb-4 flex justify-center gap-2">
                <span class="w-2 h-2 rounded-full bg-indigo-500"></span>
                <span class="w-2 h-2 rounded-full bg-purple-500"></span>
                <span class="w-2 h-2 rounded-full bg-pink-500"></span>
            </div>
            <p class="text-lg font-medium text-white">Sistem Hybrid Aktif</p>
            <p class="text-xs mt-2 font-mono text-gray-400">Ketik "gambar" untuk visual, atau tanya apa saja untuk teks.</p>
        </div>
    </main>

    <!-- Status Indicator -->
    <div id="status-bar" class="hidden px-8 py-3 flex items-center gap-3 text-[10px] font-mono text-indigo-400 uppercase tracking-widest border-t border-white/5 bg-black/80">
        <div class="flex gap-1">
            <div class="loading-pulse"></div>
            <div class="loading-pulse" style="animation-delay: 0.2s"></div>
            <div class="loading-pulse" style="animation-delay: 0.4s"></div>
        </div>
        <span id="status-text">Memproses permintaan...</span>
    </div>

    <!-- Input Area -->
    <div class="p-4 md:p-8 bg-[#050505]">
        <div class="max-w-4xl mx-auto">
            <div class="glass-card rounded-2xl p-2 flex items-end gap-2 focus-within:ring-2 ring-indigo-500/20 transition-all border-white/10">
                <textarea 
                    id="user-input"
                    rows="1"
                    placeholder="Contoh: 'Buatkan gambar naga api' atau 'Siapa presiden pertama RI?'"
                    class="flex-1 bg-transparent border-none focus:ring-0 text-white p-3 resize-none text-sm placeholder:text-gray-600"
                    oninput="this.style.height = ''; this.style.height = this.scrollHeight + 'px'"
                ></textarea>
                <button 
                    onclick="handleInput()"
                    class="bg-indigo-600 hover:bg-indigo-500 text-white px-6 py-3 rounded-xl transition-all font-bold text-xs uppercase tracking-widest flex shadow-lg shadow-indigo-600/20 mb-1 mr-1"
                >
                    Kirim
                </button>
            </div>
            <div class="flex justify-center gap-6 mt-4 opacity-30">
                <div class="flex items-center gap-1 text-[9px] text-gray-400 uppercase font-bold tracking-widest">
                    <div class="w-1 h-1 bg-white rounded-full"></div> Chat
                </div>
                <div class="flex items-center gap-1 text-[9px] text-gray-400 uppercase font-bold tracking-widest">
                    <div class="w-1 h-1 bg-white rounded-full"></div> Visual
                </div>
                <div class="flex items-center gap-1 text-[9px] text-gray-400 uppercase font-bold tracking-widest">
                    <div class="w-1 h-1 bg-white rounded-full"></div> Analysis
                </div>
            </div>
        </div>
    </div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/marked/4.3.0/marked.min.js"></script>

    <script>
        const apiKey = ""; // Kunci API disediakan secara otomatis oleh sistem

        const imgTriggers = ["buat gambar", "buatkan gambar", "generate", "lukis", "gambar", "foto", "lukisan", "tampilkan gambar"];

        async function handleInput() {
            const inputField = document.getElementById('user-input');
            const prompt = inputField.value.trim();
            if (!prompt) return;

            addMessage(prompt, true);
            inputField.value = '';
            inputField.style.height = 'auto';
            
            const statusBar = document.getElementById('status-bar');
            const statusText = document.getElementById('status-text');
            statusBar.classList.remove('hidden');

            const isImageRequest = imgTriggers.some(kw => prompt.toLowerCase().includes(kw));

            try {
                if (isImageRequest) {
                    statusText.innerText = "Membangkitkan Visual (Image Engine)...";
                    let cleanPrompt = prompt;
                    imgTriggers.forEach(kw => {
                        const reg = new RegExp(kw, 'gi');
                        cleanPrompt = cleanPrompt.replace(reg, '');
                    });
                    
                    const imageUrl = await generateImage(cleanPrompt.trim() || "A beautiful cinematic digital art");
                    addImageMessage(imageUrl, cleanPrompt.trim());
                } else {
                    statusText.innerText = "AI sedang merespon pertanyaan Anda...";
                    const response = await fetchChat(prompt);
                    addMessage(response, false);
                }
            } catch (error) {
                console.error(error);
                showError("Maaf, permintaan tidak dapat dipenuhi. Pastikan koneksi stabil atau coba gunakan prompt yang berbeda.");
            } finally {
                statusBar.classList.add('hidden');
            }
        }

        async function fetchChat(text) {
            const url = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;
            const response = await fetch(url, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ 
                    contents: [{ parts: [{ text: text }] }],
                    systemInstruction: { parts: [{ text: "Jawab dalam Bahasa Indonesia. Tetap informatif, sopan, dan singkat jika perlu." }] }
                })
            });
            
            if (!response.ok) throw new Error("Gagal Chat.");
            const data = await response.json();
            return data.candidates[0].content.parts[0].text;
        }

        async function generateImage(prompt) {
            // Menggunakan Gemini Image Preview (Lebih stabil daripada Imagen 4.0 di lingkungan ini)
            const url = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-image-preview:generateContent?key=${apiKey}`;
            
            const response = await fetch(url, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({
                    contents: [{ parts: [{ text: prompt }] }],
                    generationConfig: { responseModalities: ['TEXT', 'IMAGE'] }
                })
            });

            if (!response.ok) throw new Error("Gagal Gambar.");

            const result = await response.json();
            const base64 = result.candidates?.[0]?.content?.parts?.find(p => p.inlineData)?.inlineData?.data;
            
            if (base64) {
                return `data:image/png;base64,${base64}`;
            } else {
                throw new Error("No Image Data");
            }
        }

        function addMessage(text, isUser) {
            const chatBox = document.getElementById('chat-box');
            const div = document.createElement('div');
            div.className = `flex ${isUser ? 'justify-end' : 'justify-start'} animate-in fade-in slide-in-from-bottom-2 duration-300`;
            
            const content = isUser ? text : marked.parse(text);
            div.innerHTML = `<div class="${isUser ? 'user-msg' : 'ai-msg'} shadow-xl">${content}</div>`;
            
            chatBox.appendChild(div);
            chatBox.scrollTo({ top: chatBox.scrollHeight, behavior: 'smooth' });
        }

        function addImageMessage(url, prompt) {
            const chatBox = document.getElementById('chat-box');
            const div = document.createElement('div');
            div.className = "flex justify-start image-result";
            div.innerHTML = `
                <div class="glass-card rounded-2xl overflow-hidden p-2 w-full max-w-[420px] shadow-2xl">
                    <img src="${url}" class="w-full h-auto rounded-xl shadow-inner border border-white/5" loading="lazy">
                    <div class="p-3 flex justify-between items-center bg-black/20 mt-2 rounded-lg">
                        <p class="text-[10px] text-gray-500 italic truncate mr-4">${prompt || "AI Visual"}</p>
                        <a href="${url}" download="ai-visual.png" class="text-[10px] font-bold text-indigo-400 hover:text-indigo-200 uppercase tracking-widest">Download</a>
                    </div>
                </div>
            `;
            chatBox.appendChild(div);
            chatBox.scrollTo({ top: chatBox.scrollHeight, behavior: 'smooth' });
        }

        function showError(msg) {
            const chatBox = document.getElementById('chat-box');
            const div = document.createElement('div');
            div.className = "flex justify-start";
            div.innerHTML = `<div class="error-msg max-w-[85%] font-medium">⚠️ <span>${msg}</span></div>`;
            chatBox.appendChild(div);
            chatBox.scrollTo({ top: chatBox.scrollHeight, behavior: 'smooth' });
        }

        document.getElementById('user-input').addEventListener('keydown', function (e) {
            if (e.key === 'Enter' && !e.shiftKey) {
                e.preventDefault();
                handleInput();
            }
        });
    </script>
</body>
</html>
