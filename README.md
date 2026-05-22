<!DOCTYPE html>
<html lang="si">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KAVISHKA DIGITAL VESAK ZONE</title>
    <style>
        :root {
            --bg-color: #0a0a0c;
            --panel-bg: #141419;
            --accent-gold: #ffcc00;
            --accent-red: #ff3344;
            --text-color: #ffffff;
            --text-muted: #aaaaaa;
            --border-glow: 0 0 10px rgba(255, 204, 0, 0.3);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            overflow-x: hidden;
        }

        /* Intro Overlay Layer */
        #intro-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, #1a1a24 0%, #050508 100%);
            z-index: 99999;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            opacity: 1;
            transition: opacity 0.4s ease;
        }

        #intro-overlay h1 {
            color: var(--accent-gold);
            font-size: 2.5rem;
            margin-bottom: 20px;
            text-shadow: 0 0 20px rgba(255, 204, 0, 0.6);
            padding: 0 15px;
        }

        .enter-btn {
            background: linear-gradient(45deg, var(--accent-red), var(--accent-gold));
            color: #000;
            font-weight: bold;
            font-size: 1.3rem;
            padding: 16px 45px;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            box-shadow: 0 0 20px var(--accent-gold);
            transition: transform 0.2s, box-shadow 0.2s;
            position: relative;
            z-index: 100000;
        }

        .enter-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 0 30px var(--accent-gold);
        }

        /* Header Style */
        header {
            background-color: var(--panel-bg);
            padding: 20px;
            text-align: center;
            border-bottom: 2px solid #222;
            box-shadow: var(--border-glow);
        }

        header h1 {
            color: var(--accent-gold);
            font-size: 2rem;
            letter-spacing: 2px;
            text-shadow: 0 0 10px rgba(255, 204, 0, 0.5);
        }

        header p {
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-top: 5px;
        }

        /* Main Layout */
        .container {
            display: grid;
            grid-template-columns: 1fr;
            gap: 20px;
            padding: 20px;
            max-width: 1400px;
            margin: 0 auto;
        }

        @media (min-width: 992px) {
            .container {
                grid-template-columns: 1.2fr 1fr;
            }
        }

        /* Preview Workspace */
        .preview-panel {
            background-color: #000;
            border-radius: 12px;
            border: 1px solid #333;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 15px;
            position: relative;
            min-height: 450px;
            box-shadow: inset 0 0 30px rgba(0,0,0,0.8);
        }

        canvas {
            max-width: 100%;
            height: auto;
            border-radius: 8px;
            background-color: #030305;
        }

        /* Control Panel Styles */
        .control-panel {
            background-color: var(--panel-bg);
            border-radius: 12px;
            border: 1px solid #25252b;
            padding: 20px;
            display: flex;
            flex-direction: column;
            height: fit-content;
        }

        /* Tab Navigation */
        .tabs {
            display: flex;
            overflow-x: auto;
            gap: 10px;
            border-bottom: 1px solid #333;
            padding-bottom: 10px;
            margin-bottom: 20px;
        }

        .tabs::-webkit-scrollbar {
            height: 4px;
        }

        .tab-btn {
            background-color: #1c1c24;
            color: var(--text-muted);
            border: 1px solid #333;
            padding: 10px 16px;
            border-radius: 8px;
            cursor: pointer;
            white-space: nowrap;
            font-size: 0.9rem;
            transition: all 0.3s;
        }

        .tab-btn.active, .tab-btn:hover {
            background-color: var(--accent-gold);
            color: #000;
            font-weight: bold;
            border-color: var(--accent-gold);
        }

        /* Tool Content Panels */
        .tool-content {
            display: none;
        }

        .tool-content.active {
            display: block;
        }

        .setting-group {
            margin-bottom: 20px;
        }

        .setting-group label {
            display: block;
            font-size: 0.95rem;
            color: var(--accent-gold);
            margin-bottom: 8px;
            font-weight: 500;
        }

        .input-control {
            width: 100%;
            background-color: #1a1a24;
            border: 1px solid #333;
            color: #fff;
            padding: 12px;
            border-radius: 8px;
            outline: none;
            font-size: 0.95rem;
            margin-bottom: 5px;
        }

        /* Template Grid Selector */
        .template-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
        }

        .tpl-card {
            background-color: #1a1a24;
            border: 2px solid #333;
            border-radius: 8px;
            padding: 15px 5px;
            text-align: center;
            cursor: pointer;
            font-size: 0.85rem;
            transition: all 0.2s;
        }

        .tpl-card:hover, .tpl-card.active {
            border-color: var(--accent-gold);
            background-color: rgba(255, 204, 0, 0.1);
        }

        .tpl-icon {
            font-size: 1.8rem;
            margin-bottom: 5px;
            display: block;
        }

        /* Action Buttons */
        .btn-primary {
            background: linear-gradient(135deg, #ffcc00, #ffaa00);
            color: #000;
            border: none;
            padding: 14px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            font-size: 1rem;
            width: 100%;
            transition: opacity 0.2s;
            box-shadow: 0 4px 10px rgba(255, 204, 0, 0.2);
        }

        #export-status {
            margin-top: 15px;
            text-align: center;
            font-weight: bold;
            color: var(--accent-gold);
            display: none;
        }

        .about-box {
            background: linear-gradient(135deg, #1c1c26, #14141a);
            border-left: 4px solid var(--accent-gold);
            padding: 15px;
            border-radius: 4px;
            font-size: 0.95rem;
            line-height: 1.6;
        }

        .about-box h3 {
            color: var(--accent-gold);
            margin-bottom: 8px;
        }

        .checkbox-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
        }

        .check-item {
            display: flex;
            align-items: center;
            gap: 8px;
            background: #1a1a24;
            padding: 10px;
            border-radius: 6px;
            cursor: pointer;
        }

        .grid-inputs {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 8px;
        }
        
        /* Custom scrollbar for about section */
        .about-scroll::-webkit-scrollbar {
            width: 8px;
        }
        .about-scroll::-webkit-scrollbar-track {
            background: #141419;
        }
        .about-scroll::-webkit-scrollbar-thumb {
            background: #333;
            border-radius: 4px;
        }
        .about-scroll::-webkit-scrollbar-thumb:hover {
            background: var(--accent-gold);
        }
    </style>
</head>
<body>

    <div id="intro-overlay">
        <h1>KAVISHKA DIGITAL VESAK ZONE</h1>
        <p style="color: #aaa; margin-bottom: 30px; padding:0 20px;">දිව්‍යමය ආලෝක පූජාව සහ පූජනීය තොරන් නිර්මාණ කලාපයට ඇතුළු වන්න</p>
        <button id="mainEnterBtn" class="enter-btn">ENTER ZONE</button>
    </div>

    <header>
        <h1>KAVISHKA DIGITAL VESAK ZONE</h1>
        <p>Create & Export Your Own High-Quality Animated Digital Vesak Thorana</p>
    </header>

    <div class="container">
        <div class="preview-panel">
            <canvas id="thoranCanvas" width="1080" height="1080"></canvas>
            <p style="color: var(--text-muted); font-size: 0.8rem; margin-top: 10px;">⚡ Real-time HD Rendering Engine View</p>
        </div>

        <div class="control-panel">
            <div class="tabs">
                <button id="btn-tab-templates" class="tab-btn active">🎴 Formats</button>
                <button id="btn-tab-lights" class="tab-btn">💡 Lighting</button>
                <button id="btn-tab-decorations" class="tab-btn">🏮 Decor & Flags</button>
                <button id="btn-tab-jataka" class="tab-btn">📜 Jataka Text</button>
                <button id="btn-tab-export" class="tab-btn">💾 Export HD</button>
                <button id="btn-tab-about" class="tab-btn">ℹ️ About</button>
            </div>

            <div id="tab-templates" class="tool-content active">
                <div class="setting-group">
                    <label>Select Thorana Template Style (සාම්ප්‍රදායික හැඩතල)</label>
                    <div class="template-grid">
                        <div id="tpl1" class="tpl-card active">
                            <span class="tpl-icon">🔱</span>Arch Frame<br>(තිරස් තොරණ)
                        </div>
                        <div id="tpl2" class="tpl-card">
                            <span class="tpl-icon">🎡</span>Circular Wheel<br>(චක්‍ර තොරණ)
                        </div>
                        <div id="tpl3" class="tpl-card">
                            <span class="tpl-icon">💎</span>Diamond Star<br>(අෂ්ටාස්‍ර තොරණ)
                        </div>
                    </div>
                </div>
                <div class="setting-group">
                    <label>Upload Central Buddha Image (ප්‍රධාන බුදුරූපය)</label>
                    <input type="file" id="buddha-upload" class="input-control" accept="image/*">
                </div>
                <div class="setting-group">
                    <label>Upload Panel Images (වටේ පැනල් සඳහා පින්තූර)</label>
                    <div class="grid-inputs">
                        <input type="file" id="panel-input-0" class="input-control" accept="image/*">
                        <input type="file" id="panel-input-1" class="input-control" accept="image/*">
                        <input type="file" id="panel-input-2" class="input-control" accept="image/*">
                        <input type="file" id="panel-input-3" class="input-control" accept="image/*">
                    </div>
                    <input type="file" id="panel-input-4" class="input-control" accept="image/*" style="margin-top: 5px;">
                </div>
                <div class="setting-group">
                    <label>Upload Background Vesak Music (ගිලෙමි ඔබේ ගුණ මූදේ MP3)</label>
                    <input type="file" id="local-audio-picker" class="input-control" accept="audio/*">
                </div>
            </div>

            <div id="tab-lights" class="tool-content">
                <div class="setting-group">
                    <label>Light Chasing Patterns (විදුලි බුබුළු රටා)</label>
                    <select id="light-pattern" class="input-control">
                        <option value="wave">Wave Chasing (රැලි රටාව)</option>
                        <option value="alternate">Alternate Blinking (මාරුවෙන් මාරුවට)</option>
                        <option value="rainbow">Multi-Color Flash (වර්ණ මිශ්‍රණ)</option>
                    </select>
                </div>
                <div class="setting-group">
                    <label>Light Flash Speed</label>
                    <input type="range" id="light-speed" min="1" max="5" value="3" style="width:100%; accent-color:var(--accent-gold);">
                </div>
                <div class="setting-group">
                    <label>Ras Mala Effects (රශ්මි මාලා වළලු)</label>
                    <div class="checkbox-grid">
                        <label class="check-item">
                            <input type="checkbox" id="ras-mala-toggle" checked> Activate Rings
                        </label>
                        <label class="check-item">
                            <input type="checkbox" id="glow-toggle" checked> Neon Glow
                        </label>
                    </div>
                </div>
            </div>

            <div id="tab-decorations" class="tool-content">
                <div class="setting-group">
                    <label>Add Extra Visual Elements</label>
                    <div class="checkbox-grid">
                        <label class="check-item">
                            <input type="checkbox" id="flag-toggle" checked> Buddhist Flags
                        </label>
                        <label class="check-item">
                            <input type="checkbox" id="lantern-toggle" checked> Vesak Lanterns
                        </label>
                        <label class="check-item">
                            <input type="checkbox" id="oil-lamp-toggle" checked> Clay Oil Lamps
                        </label>
                        <label class="check-item">
                            <input type="checkbox" id="sparkle-toggle" checked> Falling Sparkles
                        </label>
                    </div>
                </div>
            </div>

            <div id="tab-jataka" class="tool-content">
                <div class="setting-group">
                    <label>Jataka Narrative Title (ජාතක කථාවේ නම)</label>
                    <input type="text" id="jataka-title" class="input-control" value="මහාසීලව ජාතක කථා පුවත">
                </div>
                <div class="setting-group">
                    <label>Description Text Box (තොරණ විස්තරය)</label>
                    <textarea id="jataka-desc" class="input-control" rows="4" style="resize:none;">පින්වත්නි, මහාසීලව රජතුමා තමන්ව මරන්නට පැමිණි සතුරන්ට පවා මෛත්‍රිය දැක්වූ සේක. අවසානයේ ඉවසීම සහ ගුණය නිසාම නැවතත් තමන්ගේ රාජ්‍යය ජයග්‍රහණය කිරීමට එතුමා සමත් විය.</textarea>
                </div>
            </div>

            <div id="tab-export" class="tool-content">
                <div class="setting-group">
                    <label>Video Output Ratio</label>
                    <select id="export-ratio" class="input-control">
                        <option value="11">1:1 Square (FB / Insta Post)</option>
                        <option value="169">16:9 Landscape (YouTube HD)</option>
                        <option value="916">9:16 Vertical (TikTok / Reels)</option>
                    </select>
                </div>
                <div class="setting-group">
                    <label>Target Video Duration</label>
                    <select id="export-duration" class="input-control">
                        <option value="20">20 Seconds Video</option>
                        <option value="40">40 Seconds Video</option>
                        <option value="60">60 Seconds Video</option>
                    </select>
                </div>
                <button id="startExportBtn" class="btn-primary">🎥 START EXPORTING FULL HD VIDEO</button>
                <div id="export-status">Processing and recording canvas loop... please wait.</div>
            </div>

            <div id="tab-about" class="tool-content">
                <div class="about-box about-scroll" style="max-height: 500px; overflow-y: auto;">
                    <h3 style="font-size: 1.3rem;">🪷 Kavishka Digital Vesak Zone</h3>
                    <p style="margin-top: 10px; font-size: 0.95rem;">Welcome to the <strong>Kavishka Digital Vesak Zone</strong>, an interactive web-based tool to create, customize, and export your own High-Quality Animated Digital Vesak Thorana (Pandol).</p>

                    <h4 style="color: var(--accent-gold); margin-top: 20px; margin-bottom: 10px;">✨ Features</h4>
                    <ul style="margin-left: 20px; font-size: 0.9rem; line-height: 1.6;">
                        <li><strong>Real-time Engine:</strong> Live HD rendering of your Vesak Thorana directly in the browser.</li>
                        <li><strong>Customizable Templates:</strong> Choose between Traditional Arch Frame (තිරස් තොරණ), Circular Wheel (චක්‍ර තොරණ), or Diamond Star (අෂ්ටාස්‍ර තොරණ).</li>
                        <li><strong>Personalized Uploads:</strong> Add your own Central Buddha image and surrounding Jataka panel images.</li>
                        <li><strong>Dynamic Lighting:</strong> Control bulb chasing patterns, flash speeds, and activate neon glows or Ras Mala (රශ්මි මාලා).</li>
                        <li><strong>Decorations & Audio:</strong> Add Buddhist flags, lanterns, oil lamps, falling sparkles, and background Vesak MP3 tracks.</li>
                        <li><strong>Video Export:</strong> Record and export your creation directly as a Full HD Video (Square 1:1, Landscape 16:9, or Vertical 9:16) for social media!</li>
                    </ul>

                    <h4 style="color: var(--accent-gold); margin-top: 20px; margin-bottom: 10px;">🚀 How to Run</h4>
                    <ol style="margin-left: 20px; font-size: 0.9rem; line-height: 1.6;">
                        <li>Download or clone this repository.</li>
                        <li>Open the <code>index.html</code> file in any modern web browser (Google Chrome, Edge, Safari).</li>
                        <li>Click <strong>"ENTER ZONE"</strong>.</li>
                        <li>Use the control panel on the right to customize your Thorana, upload images, and add background music.</li>
                        <li>Go to the "Export HD" tab to download your customized video.</li>
                    </ol>

                    <h4 style="color: var(--accent-gold); margin-top: 20px; margin-bottom: 10px;">🛠️ Technologies Used</h4>
                    <ul style="margin-left: 20px; font-size: 0.9rem; line-height: 1.6;">
                        <li><strong>HTML5 Canvas</strong> (For real-time graphics rendering)</li>
                        <li><strong>CSS3</strong> (For responsive UI and glowing elements)</li>
                        <li><strong>Vanilla JavaScript</strong> (For animation logic and MediaRecorder video export)</li>
                    </ul>

                    <hr style="border-color: #333; margin: 20px 0;">
                    <p style="text-align: center; font-size: 1.1rem; color: var(--accent-gold);"><strong>Developed by Kavishka</strong></p>
                </div>
            </div>
        </div>
    </div>

    <audio id="vesakAudio" loop></audio>

    <script>
        document.addEventListener("DOMContentLoaded", function () {
            const canvas = document.getElementById('thoranCanvas');
            const ctx = canvas.getContext('2d');
            const audio = document.getElementById('vesakAudio');

            let currentTemplate = 1;
            let rotationAngle = 0;
            let colorTick = 0;
            let buddhaImage = null;
            let panelImages = [null, null, null, null, null];

            // 🔴 Safe Event Bindings to Prevent DOM Errors
            document.getElementById('mainEnterBtn').addEventListener('click', startDigitalVesakZone);
            document.getElementById('local-audio-picker').addEventListener('change', loadLocalAudio);
            document.getElementById('export-ratio').addEventListener('change', adjustRatio);
            document.getElementById('buddha-upload').addEventListener('change', loadUserBuddhaImage);
            document.getElementById('startExportBtn').addEventListener('click', exportThoranaVideo);

            for (let i = 0; i < 5; i++) {
                let el = document.getElementById(`panel-input-${i}`);
                if (el) {
                    el.addEventListener('change', function (e) {
                        loadPanelImage(e, i);
                    });
                }
            }

            // Tab navigation switching
            const tabs = ['templates', 'lights', 'decorations', 'jataka', 'export', 'about'];
            tabs.forEach(tab => {
                let btn = document.getElementById(`btn-tab-${tab}`);
                if (btn) {
                    btn.addEventListener('click', function (e) {
                        switchTab(e, `tab-${tab}`);
                    });
                }
            });

            document.getElementById('tpl1').addEventListener('click', function () { setTemplate(1, this); });
            document.getElementById('tpl2').addEventListener('click', function () { setTemplate(2, this); });
            document.getElementById('tpl3').addEventListener('click', function () { setTemplate(3, this); });

            // Start animation loop immediately
            animateWorkspaceLoop();

            function startDigitalVesakZone() {
                const overlay = document.getElementById('intro-overlay');
                if (overlay) {
                    overlay.style.opacity = '0';
                    setTimeout(() => { overlay.style.display = 'none'; }, 400);
                }
                try {
                    if (audio && audio.src) {
                        audio.play().catch(e => console.log("Audio waiting for user file."));
                    }
                } catch (e) { console.log("Audio safety trigger."); }
            }

            function loadLocalAudio(e) {
                if (e.target.files && e.target.files[0]) {
                    const file = e.target.files[0];
                    const url = URL.createObjectURL(file);
                    audio.src = url;
                    audio.play().catch(err => console.log("Playback interaction required."));
                }
            }

            function switchTab(evt, tabId) {
                const contents = document.getElementsByClassName('tool-content');
                for (let i = 0; i < contents.length; i++) contents[i].classList.remove('active');
                const tabBtns = document.getElementsByClassName('tab-btn');
                for (let i = 0; i < tabBtns.length; i++) tabBtns[i].classList.remove('active');
                document.getElementById(tabId).classList.add('active');
                evt.currentTarget.classList.add('active');
            }

            function setTemplate(id, element) {
                currentTemplate = id;
                const cards = document.getElementsByClassName('tpl-card');
                for (let card of cards) card.classList.remove('active');
                element.classList.add('active');
            }

            function adjustRatio() {
                const ratio = document.getElementById('export-ratio').value;
                if (ratio === "11") { canvas.width = 1080; canvas.height = 1080; }
                else if (ratio === "169") { canvas.width = 1920; canvas.height = 1080; }
                else if (ratio === "916") { canvas.width = 1080; canvas.height = 1920; }
            }

            function loadUserBuddhaImage(e) {
                if (e.target.files && e.target.files[0]) {
                    const reader = new FileReader();
                    reader.onload = function (event) {
                        buddhaImage = new Image();
                        buddhaImage.src = event.target.result;
                    }
                    reader.readAsDataURL(e.target.files[0]);
                }
            }

            function loadPanelImage(e, index) {
                if (e.target.files && e.target.files[0]) {
                    const reader = new FileReader();
                    reader.onload = function (event) {
                        panelImages[index] = new Image();
                        panelImages[index].src = event.target.result;
                    }
                    reader.readAsDataURL(e.target.files[0]);
                }
            }

            function varColor(index) {
                const pattern = document.getElementById('light-pattern').value;
                if (pattern === "rainbow") {
                    const hues = [0, 45, 120, 200, 280, 330];
                    return `hsl(${hues[(Math.floor(colorTick) + index) % hues.length]}, 100%, 60%)`;
                }
                return index % 2 === 0 ? "#ffcc00" : "#ff3344";
            }

            function drawThorana() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                let bgGrad = ctx.createRadialGradient(canvas.width / 2, canvas.height / 3, 50, canvas.width / 2, canvas.height / 3, canvas.width * 0.8);
                bgGrad.addColorStop(0, '#040408');
                bgGrad.addColorStop(1, '#000000');
                ctx.fillStyle = bgGrad;
                ctx.fillRect(0, 0, canvas.width, canvas.height);

                const centerX = canvas.width / 2;
                const centerY = canvas.height / 2.3;
                const speed = parseInt(document.getElementById('light-speed').value);
                colorTick += speed * 0.05;

                if (document.getElementById('sparkle-toggle').checked) {
                    for (let i = 0; i < 20; i++) {
                        let sx = Math.sin(colorTick + i) * canvas.width / 2 + centerX;
                        let sy = ((colorTick * 20 + i * 50) % canvas.height);
                        ctx.fillStyle = `rgba(255, 255, 200, ${Math.abs(Math.sin(colorTick + i))})`;
                        ctx.fillRect(sx, sy, 4, 4);
                    }
                }

                if (document.getElementById('flag-toggle').checked) drawBuddhistFlags();

                if (currentTemplate === 1) drawArchTemplate(centerX, centerY);
                else if (currentTemplate === 2) drawWheelTemplate(centerX, centerY);
                else drawDiamondTemplate(centerX, centerY);

                if (document.getElementById('ras-mala-toggle').checked) {
                    rotationAngle += 0.02;
                    ctx.save();
                    ctx.translate(centerX, centerY);
                    ctx.rotate(rotationAngle);
                    if (document.getElementById('glow-toggle').checked) {
                        ctx.shadowBlur = 25;
                        ctx.shadowColor = "#ffcc00";
                    }
                    for (let r = 0; r < 6; r++) {
                        ctx.strokeStyle = r % 2 === 0 ? "rgba(255,170,0,0.8)" : "rgba(255,50,50,0.7)";
                        ctx.lineWidth = 4;
                        ctx.beginPath();
                        for (let i = 0; i < 24; i++) {
                            let angle = (i * Math.PI / 12);
                            let ext = (r * 15) + (Math.sin(colorTick + r) * 10) + 120;
                            ctx.moveTo(0, 0);
                            ctx.lineTo(Math.cos(angle) * ext, Math.sin(angle) * ext);
                        }
                        ctx.stroke();
                    }
                    ctx.restore();
                    ctx.shadowBlur = 0;
                }

                ctx.save();
                if (buddhaImage) {
                    ctx.beginPath();
                    ctx.arc(centerX, centerY, 100, 0, Math.PI * 2);
                    ctx.clip();
                    ctx.drawImage(buddhaImage, centerX - 100, centerY - 100, 200, 200);
                } else {
                    ctx.fillStyle = "#ffaa00";
                    ctx.beginPath();
                    ctx.arc(centerX, centerY, 80, 0, Math.PI * 2);
                    ctx.fill();
                    ctx.fillStyle = "#fff";
                    ctx.font = "bold 20px sans-serif";
                    ctx.textAlign = "center";
                    ctx.fillText("BUDDHA", centerX, centerY + 8);
                }
                ctx.restore();

                drawNarrativePanel();

                if (document.getElementById('lantern-toggle').checked) drawSideLanterns(centerX, centerY);
                if (document.getElementById('oil-lamp-toggle').checked) drawTraditionalLamps();
            }

            function drawArchTemplate(cx, cy) {
                const panels = [
                    { x: cx - 320, y: cy + 100, r: 80 },
                    { x: cx + 320, y: cy + 100, r: 80 },
                    { x: cx - 240, y: cy - 180, r: 90 },
                    { x: cx + 240, y: cy - 180, r: 90 },
                    { x: cx, y: cy - 300, r: 110 }
                ];
                panels.forEach((p, idx) => {
                    ctx.save();
                    ctx.fillStyle = "#161622";
                    ctx.strokeStyle = varColor(idx);
                    ctx.lineWidth = 6;
                    ctx.beginPath();
                    ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
                    ctx.fill();
                    ctx.stroke();
                    if (panelImages[idx]) {
                        ctx.clip();
                        ctx.drawImage(panelImages[idx], p.x - p.r, p.y - p.r, p.r * 2, p.r * 2);
                    } else {
                        ctx.fillStyle = "rgba(255,204,0,0.15)";
                        ctx.fill();
                    }
                    ctx.restore();
                    drawBulbRing(p.x, p.y, p.r + 10, idx);
                });
            }

            function drawWheelTemplate(cx, cy) {
                ctx.strokeStyle = "#ff3344";
                ctx.lineWidth = 8;
                ctx.beginPath();
                ctx.arc(cx, cy, 340, 0, Math.PI * 2);
                ctx.stroke();

                for (let i = 0; i < 8; i++) {
                    let angle = (i * Math.PI / 4) + (colorTick * 0.02);
                    let px = cx + Math.cos(angle) * 240;
                    let py = cy + Math.sin(angle) * 240;

                    ctx.save();
                    ctx.fillStyle = "#11111a";
                    ctx.strokeStyle = varColor(i);
                    ctx.lineWidth = 4;
                    ctx.beginPath();
                    ctx.arc(px, py, 70, 0, Math.PI * 2);
                    ctx.fill();
                    ctx.stroke();

                    let imgIdx = i % 5;
                    if (panelImages[imgIdx]) {
                        ctx.clip();
                        ctx.drawImage(panelImages[imgIdx], px - 70, py - 70, 140, 140);
                    }
                    ctx.restore();
                    drawBulbRing(px, py, 78, i);
                }
            }

            function drawDiamondTemplate(cx, cy) {
                for (let i = 0; i < 6; i++) {
                    let offset = i * 90;
                    ctx.strokeStyle = varColor(i);
                    ctx.lineWidth = 5;
                    ctx.strokeRect(cx - 150 - offset / 2, cy - 150 - offset / 2, 300 + offset, 300 + offset);
                    drawFlashBulb(cx - 150 - offset / 2, cy - 150 - offset / 2, i);
                    drawFlashBulb(cx + 150 + offset / 2, cy - 150 - offset / 2, i);
                    drawFlashBulb(cx - 150 - offset / 2, cy + 150 + offset / 2, i);
                    drawFlashBulb(cx + 150 + offset / 2, cy + 150 + offset / 2, i);
                }
            }

            function drawBulbRing(x, y, radius, group) {
                const numBulbs = 20;
                const pattern = document.getElementById('light-pattern').value;
                for (let i = 0; i < numBulbs; i++) {
                    let angle = (i * Math.PI * 2 / numBulbs);
                    let bx = x + Math.cos(angle) * radius;
                    let by = y + Math.sin(angle) * radius;
                    let isOn = true;
                    if (pattern === "alternate") isOn = (Math.floor(colorTick) + i) % 2 === 0;
                    else if (pattern === "wave") isOn = Math.sin(colorTick + (i * 0.5) + group) > 0;

                    ctx.fillStyle = isOn ? varColor(i + group) : "#333333";
                    ctx.beginPath();
                    ctx.arc(bx, by, 7, 0, Math.PI * 2);
                    ctx.fill();
                }
            }

            function drawFlashBulb(x, y, step) {
                ctx.fillStyle = (Math.floor(colorTick) + step) % 2 === 0 ? "#ffcc00" : "#ff3344";
                ctx.beginPath();
                ctx.arc(x, y, 9, 0, Math.PI * 2);
                ctx.fill();
            }

            function drawBuddhistFlags() {
                const colors = ["#0033cc", "#ffcc00", "#ff3333", "#ffffff", "#ff6600"];
                let fw = canvas.width / 15;
                for (let i = 0; i < 15; i++) {
                    ctx.fillStyle = colors[i % colors.length];
                    ctx.fillRect(i * fw, 0, fw, 25);
                }
            }

            function drawSideLanterns(cx, cy) {
                let lx1 = cx - 440; let lx2 = cx + 440; let ly = cy + 250;
                let h = 60 + Math.sin(colorTick) * 5;
                [lx1, lx2].forEach(x => {
                    ctx.strokeStyle = "#ffaa00"; ctx.lineWidth = 3;
                    ctx.beginPath(); ctx.moveTo(x, ly - 50); ctx.lineTo(x, ly); ctx.stroke();
                    ctx.fillStyle = "#ff5533"; ctx.beginPath(); ctx.moveTo(x, ly);
                    ctx.lineTo(x - 30, ly + 40); ctx.lineTo(x + 30, ly + 40); ctx.closePath(); ctx.fill();
                    ctx.fillStyle = "#ffcc00"; ctx.fillRect(x - 30, ly + 40, 60, h);
                });
            }

            function drawTraditionalLamps() {
                let bottomY = canvas.height - 300;
                if (canvas.height > 1200) bottomY = canvas.height - 550;
                for (let i = 0; i < 5; i++) {
                    let lx = (canvas.width / 6) * (i + 1);
                    ctx.fillStyle = "#8b4513"; ctx.beginPath();
                    ctx.ellipse(lx, bottomY, 35, 15, 0, 0, Math.PI, false); ctx.fill();
                    ctx.fillStyle = Math.random() > 0.5 ? "#ffcc00" : "#ff3300"; ctx.beginPath(); ctx.moveTo(lx, bottomY - 10);
                    ctx.quadraticCurveTo(lx - 12, bottomY - 25, lx, bottomY - 45); ctx.quadraticCurveTo(lx + 12, bottomY - 25, lx, bottomY - 10); ctx.fill();
                }
            }

            function drawNarrativePanel() {
                let boxWidth = canvas.width * 0.85; let boxHeight = 180;
                let bx = (canvas.width - boxWidth) / 2; let by = canvas.height - boxHeight - 50;
                if (canvas.height > 1200) by = canvas.height - boxHeight - 250;

                ctx.fillStyle = "rgba(16, 16, 24, 0.9)"; ctx.strokeStyle = "#ffcc00"; ctx.lineWidth = 5;
                ctx.shadowBlur = 15; ctx.shadowColor = "#ffaa00"; ctx.fillRect(bx, by, boxWidth, boxHeight); ctx.stroke(); ctx.shadowBlur = 0;
                ctx.strokeStyle = "#ff3344"; ctx.lineWidth = 2; ctx.strokeRect(bx + 6, by + 6, boxWidth - 12, boxHeight - 12);
                ctx.fillStyle = "#ffcc00"; ctx.font = "bold 26px sans-serif"; ctx.textAlign = "center";
                ctx.fillText(document.getElementById('jataka-title').value, canvas.width / 2, by + 45);
                ctx.fillStyle = "#ffffff"; ctx.font = "20px sans-serif";
                wrapText(ctx, document.getElementById('jataka-desc').value, canvas.width / 2, by + 90, boxWidth - 60, 30);
            }

            function wrapText(context, text, x, y, maxWidth, lineHeight) {
                let words = text.split(' '); let line = '';
                for (let n = 0; n < words.length; n++) {
                    let testLine = line + words[n] + ' ';
                    let metrics = context.measureText(testLine);
                    if (metrics.width > maxWidth && n > 0) {
                        context.fillText(line, x, y); line = words[n] + ' '; y += lineHeight;
                    } else { line = testLine; }
                }
                context.fillText(line, x, y);
            }

            function animateWorkspaceLoop() {
                drawThorana();
                requestAnimationFrame(animateWorkspaceLoop);
            }

            function exportThoranaVideo() {
                const statusLabel = document.getElementById('export-status');
                statusLabel.style.display = "block";
                statusLabel.innerText = "Initializing Video Capture Stream Engine...";

                const duration = parseInt(document.getElementById('export-duration').value);
                const stream = canvas.captureStream(30);

                let options = { mimeType: 'video/webm;codecs=vp9,opus' };
                if (!MediaRecorder.isTypeSupported(options.mimeType)) {
                    options = { mimeType: 'video/webm;codecs=vp8' };
                }

                const recorder = new MediaRecorder(stream, options);
                const chunks = [];
                recorder.ondataavailable = (e) => { if (e.data && e.data.size > 0) chunks.push(e.data); };

                recorder.onstop = () => {
                    statusLabel.innerText = "Compiling elements and processing download...";
                    const blob = new Blob(chunks, { type: 'video/mp4' });
                    const url = URL.createObjectURL(blob);
                    const a = document.createElement('a');
                    a.href = url;
                    a.download = `Kavishka_Digital_Vesak_Thorana_${Date.now()}.mp4`;
                    document.body.appendChild(a); a.click(); document.body.removeChild(a);
                    statusLabel.innerText = "✅ High-Definition Video Exported Successfully!";
                    setTimeout(() => { statusLabel.style.display = "none"; }, 5000);
                };

                recorder.start();
                let elapsed = 0;
                const countdownInterval = setInterval(() => {
                    elapsed++;
                    statusLabel.innerText = `🎥 Exporting WebM/MP4 HD Video... (${elapsed}/${duration}s Recorded)`;
                    if (elapsed >= duration) {
                        clearInterval(countdownInterval);
                        recorder.stop();
                    }
                }, 1000);
            }
        });
    </script>
</body>
</html>