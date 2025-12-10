<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>印象派鸟类乐园 | 自然之声</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #e6e6fa 0%, #f5f5dc 50%, #e0f7fa 100%);
            min-height: 100vh;
            overflow-x: hidden;
            color: #5a4a42;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            margin-bottom: 40px;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.7);
            border-radius: 20px;
            backdrop-filter: blur(10px);
            box-shadow: 0 8px 32px rgba(31, 38, 135, 0.15);
            border: 1px solid rgba(255, 255, 255, 0.3);
        }
        
        h1 {
            font-size: 3.5rem;
            color: #6b5b4d;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
            letter-spacing: 2px;
            background: linear-gradient(90deg, #8b7355, #6b5b4d, #8b7355);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .subtitle {
            font-size: 1.3rem;
            color: #8b7d6b;
            font-style: italic;
            margin-bottom: 20px;
        }
        
        .description {
            max-width: 800px;
            margin: 0 auto;
            line-height: 1.6;
            font-size: 1.1rem;
            color: #7d6d5e;
        }
        
        .content-wrapper {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            margin-bottom: 40px;
        }
        
        .bird-gallery {
            flex: 1;
            min-width: 300px;
            background-color: rgba(255, 255, 255, 0.7);
            border-radius: 20px;
            padding: 25px;
            backdrop-filter: blur(10px);
            box-shadow: 0 8px 32px rgba(31, 38, 135, 0.15);
            border: 1px solid rgba(255, 255, 255, 0.3);
        }
        
        .gallery-title {
            font-size: 1.8rem;
            color: #6b5b4d;
            margin-bottom: 20px;
            text-align: center;
            border-bottom: 2px dashed #d7ccc8;
            padding-bottom: 10px;
        }
        
        .birds-container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
        }
        
        .bird-card {
            width: 160px;
            height: 200px;
            position: relative;
            border-radius: 15px;
            overflow: hidden;
            cursor: pointer;
            transition: all 0.4s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .bird-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
        }
        
        .bird-card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            filter: sepia(0.2) contrast(1.1) brightness(1.05);
            transition: filter 0.3s ease;
        }
        
        .bird-card:hover img {
            filter: sepia(0) contrast(1.2) brightness(1.1);
        }
        
        .bird-name {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(107, 91, 77, 0.85);
            color: #f5f5f5;
            padding: 8px;
            text-align: center;
            font-size: 0.9rem;
            backdrop-filter: blur(5px);
        }
        
        .player-section {
            flex: 1;
            min-width: 300px;
            background-color: rgba(255, 255, 255, 0.7);
            border-radius: 20px;
            padding: 25px;
            backdrop-filter: blur(10px);
            box-shadow: 0 8px 32px rgba(31, 38, 135, 0.15);
            border: 1px solid rgba(255, 255, 255, 0.3);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        
        .player-title {
            font-size: 1.8rem;
            color: #6b5b4d;
            margin-bottom: 20px;
            text-align: center;
            border-bottom: 2px dashed #d7ccc8;
            padding-bottom: 10px;
            width: 100%;
        }
        
        .player-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 100%;
            max-width: 400px;
        }
        
        .album-art {
            width: 250px;
            height: 250px;
            border-radius: 20px;
            overflow: hidden;
            margin-bottom: 25px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
            position: relative;
        }
        
        .album-art img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            filter: sepia(0.3) brightness(1.05);
        }
        
        .album-art::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, rgba(139, 115, 85, 0.1), rgba(224, 247, 250, 0.2));
            pointer-events: none;
        }
        
        .song-info {
            text-align: center;
            margin-bottom: 25px;
            width: 100%;
        }
        
        .song-title {
            font-size: 1.6rem;
            color: #6b5b4d;
            margin-bottom: 5px;
        }
        
        .song-artist {
            font-size: 1.1rem;
            color: #8b7d6b;
            font-style: italic;
        }
        
        .controls {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 20px;
            margin-bottom: 20px;
            width: 100%;
        }
        
        .control-btn {
            background: rgba(107, 91, 77, 0.8);
            color: white;
            border: none;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .control-btn:hover {
            background: rgba(139, 115, 85, 0.9);
            transform: scale(1.1);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
        }
        
        .play-btn {
            width: 80px;
            height: 80px;
            font-size: 2rem;
            background: linear-gradient(135deg, #8b7355, #6b5b4d);
        }
        
        .play-btn:hover {
            background: linear-gradient(135deg, #9c8363, #7b6b5d);
        }
        
        .progress-container {
            width: 100%;
            margin-bottom: 25px;
        }
        
        .progress-bar {
            width: 100%;
            height: 8px;
            background-color: rgba(139, 115, 85, 0.2);
            border-radius: 4px;
            overflow: hidden;
            cursor: pointer;
        }
        
        .progress {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, #8b7355, #6b5b4d);
            border-radius: 4px;
            transition: width 0.1s linear;
        }
        
        .time-info {
            display: flex;
            justify-content: space-between;
            margin-top: 8px;
            font-size: 0.9rem;
            color: #7d6d5e;
        }
        
        .volume-container {
            display: flex;
            align-items: center;
            gap: 10px;
            width: 100%;
            margin-top: 10px;
        }
        
        .volume-slider {
            flex: 1;
            height: 6px;
            -webkit-appearance: none;
            appearance: none;
            background: rgba(139, 115, 85, 0.2);
            border-radius: 3px;
            outline: none;
        }
        
        .volume-slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 18px;
            height: 18px;
            border-radius: 50%;
            background: #6b5b4d;
            cursor: pointer;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }
        
        .volume-slider::-moz-range-thumb {
            width: 18px;
            height: 18px;
            border-radius: 50%;
            background: #6b5b4d;
            cursor: pointer;
            border: none;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }
        
        .instructions {
            background-color: rgba(255, 255, 255, 0.7);
            border-radius: 20px;
            padding: 25px;
            backdrop-filter: blur(10px);
            box-shadow: 0 8px 32px rgba(31, 38, 135, 0.15);
            border: 1px solid rgba(255, 255, 255, 0.3);
            margin-top: 20px;
        }
        
        .instructions h2 {
            font-size: 1.8rem;
            color: #6b5b4d;
            margin-bottom: 15px;
            border-bottom: 2px dashed #d7ccc8;
            padding-bottom: 10px;
        }
        
        .instructions ol {
            padding-left: 20px;
            margin-bottom: 15px;
        }
        
        .instructions li {
            margin-bottom: 10px;
            line-height: 1.5;
            color: #7d6d5e;
        }
        
        .instructions code {
            background-color: rgba(107, 91, 77, 0.1);
            padding: 2px 6px;
            border-radius: 4px;
            font-family: monospace;
            color: #6b5b4d;
        }
        
        .click-effect {
            position: absolute;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(255, 215, 0, 0.8) 0%, rgba(255, 215, 0, 0) 70%);
            pointer-events: none;
            animation: ripple 0.6s ease-out;
            z-index: 1000;
        }
        
        @keyframes ripple {
            0% {
                transform: scale(0.1);
                opacity: 1;
            }
            100% {
                transform: scale(4);
                opacity: 0;
            }
        }
        
        footer {
            text-align: center;
            margin-top: 40px;
            padding: 20px;
            color: #8b7d6b;
            font-size: 0.9rem;
            border-top: 1px dashed #d7ccc8;
        }
        
        @media (max-width: 768px) {
            .content-wrapper {
                flex-direction: column;
            }
            
            h1 {
                font-size: 2.5rem;
            }
            
            .bird-card {
                width: 140px;
                height: 180px;
            }
        }
        
        /* 印象派模糊效果 */
        .impressionist-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
        }
        
        .blob {
            position: absolute;
            border-radius: 50%;
            filter: blur(40px);
            opacity: 0.4;
        }
        
        .blob-1 {
            width: 300px;
            height: 300px;
            background: #e6e6fa;
            top: 10%;
            left: 5%;
        }
        
        .blob-2 {
            width: 250px;
            height: 250px;
            background: #f5f5dc;
            top: 60%;
            right: 10%;
        }
        
        .blob-3 {
            width: 350px;
            height: 350px;
            background: #e0f7fa;
            bottom: 10%;
            left: 15%;
        }
        
        .bird-card:nth-child(odd) {
            transform: rotate(-2deg);
        }
        
        .bird-card:nth-child(even) {
            transform: rotate(2deg);
        }
        
        .bird-card:hover:nth-child(odd) {
            transform: rotate(-2deg) translateY(-10px);
        }
        
        .bird-card:hover:nth-child(even) {
            transform: rotate(2deg) translateY(-10px);
        }
    </style>
</head>
<body>
    <!-- 印象派背景 -->
    <div class="impressionist-bg">
        <div class="blob blob-1"></div>
        <div class="blob blob-2"></div>
        <div class="blob blob-3"></div>
    </div>
    
    <div class="container">
        <header>
            <h1>印象派鸟类乐园</h1>
            <div class="subtitle">聆听自然之音，感受艺术之美</div>
            <p class="description">
                欢迎来到印象派鸟类主题音乐空间。在这里，您可以欣赏到美丽的鸟类插图，并聆听一首精心挑选的自然主题音乐。
                点击播放按钮开始您的视听之旅，点击鸟类图片可以触发特殊效果。
            </p>
        </header>
        
        <div class="content-wrapper">
            <div class="bird-gallery">
                <h2 class="gallery-title">鸟类插图集</h2>
                <div class="birds-container">
                    <!-- 鸟类卡片将通过JavaScript动态生成 -->
                </div>
            </div>
            
            <div class="player-section">
                <h2 class="player-title">自然之声播放器</h2>
                <div class="player-container">
                    <div class="album-art">
                        <img id="album-art-img" src="https://images.unsplash.com/photo-1511671782779-c97d3d27a1d4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80" alt="专辑封面">
                    </div>
                    
                    <div class="song-info">
                        <h3 class="song-title" id="song-title">清晨鸟鸣</h3>
                        <p class="song-artist" id="song-artist">自然之声合集</p>
                    </div>
                    
                    <div class="controls">
                        <button class="control-btn prev-btn">
                            <i class="fas fa-step-backward"></i>
                        </button>
                        
                        <button class="control-btn play-btn" id="play-btn">
                            <i class="fas fa-play"></i>
                        </button>
                        
                        <button class="control-btn next-btn">
                            <i class="fas fa-step-forward"></i>
                        </button>
                    </div>
                    
                    <div class="progress-container">
                        <div class="progress-bar" id="progress-bar">
                            <div class="progress" id="progress"></div>
                        </div>
                        <div class="time-info">
                            <span class="current-time" id="current-time">0:00</span>
                            <span class="duration" id="duration">0:00</span>
                        </div>
                    </div>
                    
                    <div class="volume-container">
                        <i class="fas fa-volume-up" style="color: #6b5b4d;"></i>
                        <input type="range" class="volume-slider" id="volume-slider" min="0" max="100" value="70">
                    </div>
                </div>
            </div>
        </div>
        
        <div class="instructions">
            <h2>如何上传自己的歌曲</h2>
            <ol>
                <li>准备您的音乐文件（支持MP3, WAV, OGG格式）</li>
                <li>将音乐文件重命名为 <code>my-song.mp3</code>（根据实际格式）</li>
                <li>将文件放置在与本HTML文件相同的目录中</li>
                <li>在JavaScript代码中，将 <code>audio.src</code> 的值改为您的文件名</li>
                <li>您还可以更新歌曲信息（标题、艺术家、专辑封面）</li>
            </ol>
            <p>提示：您也可以使用在线音乐URL，只需将 <code>audio.src</code> 设置为完整的URL地址即可。</p>
        </div>
        
        <footer>
            <p>© 2023 印象派鸟类乐园 | 本页面使用HTML5、CSS3和JavaScript构建</p>
            <p>所有插图仅供展示，音乐文件需用户自行提供</p>
        </footer>
    </div>
    
    <!-- 音频元素 -->
    <audio id="audio-player">
        <!-- 默认音频源，使用免费的鸟鸣音乐 -->
        <!-- 如果这个链接失效，请替换为下面备选链接 -->
        <source src="https://assets.mixkit.co/music/preview/mixkit-tree-of-life-2215.mp3" type="audio/mpeg">
        您的浏览器不支持音频播放。
    </audio>
    
    <script>
        // 鸟类数据 - 使用免费的鸟类图片
        const birds = [
            { name: "蓝冠鸦", img: "https://images.unsplash.com/photo-1549608276-5786777e7127?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" },
            { name: "红雀", img: "https://images.unsplash.com/photo-1551085254-e96b210db58a?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" },
            { name: "蜂鸟", img: "https://images.unsplash.com/photo-1531875506261-6d3f50b7c1c9?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" },
            { name: "猫头鹰", img: "https://images.unsplash.com/photo-1512546321483-c0468b7b8a95?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" },
            { name: "天鹅", img: "https://images.unsplash.com/photo-1599159340654-f3b0dfd6e8d4?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" },
            { name: "孔雀", img: "https://images.unsplash.com/photo-1573865526739-10659fec78a5?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" }
        ];
        
        // 音乐播放器元素
        const audioPlayer = document.getElementById('audio-player');
        const playBtn = document.getElementById('play-btn');
        const prevBtn = document.querySelector('.prev-btn');
        const nextBtn = document.querySelector('.next-btn');
        const progressBar = document.getElementById('progress-bar');
        const progress = document.getElementById('progress');
        const currentTimeEl = document.getElementById('current-time');
        const durationEl = document.getElementById('duration');
        const volumeSlider = document.getElementById('volume-slider');
        const songTitle = document.getElementById('song-title');
        const songArtist = document.getElementById('song-artist');
        const albumArtImg = document.getElementById('album-art-img');
        
        // 歌曲列表 - 使用免费的音乐和封面
        const songs = [
            {
                title: "清晨鸟鸣",
                artist: "自然之声合集",
                src: "https://assets.mixkit.co/music/preview/mixkit-tree-of-life-2215.mp3",
                cover: "https://images.unsplash.com/photo-1511671782779-c97d3d27a1d4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80"
            },
            {
                title: "林间漫步",
                artist: "宁静自然",
                src: "https://assets.mixkit.co/music/preview/mixkit-sunny-day-207.mp3",
                cover: "https://images.unsplash.com/photo-1502134249126-9f3755a50d78?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80"
            },
            {
                title: "湖畔晨曦",
                artist: "自然冥想",
                src: "https://assets.mixkit.co/music/preview/mixkit-clearing-the-skies-124.mp3",
                cover: "https://images.unsplash.com/photo-1475924156734-496f6cac6ec1?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80"
            }
        ];
        
        // 备选音乐链接（如果上面的链接失效，可以替换为这些）
        const backupSongs = [
            {
                title: "森林之音",
                artist: "自然录音",
                src: "https://assets.mixkit.co/music/preview/mixkit-deep-urban-623.mp3",
                cover: "https://images.unsplash.com/photo-1448375240586-882707db888b?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80"
            },
            {
                title: "宁静山谷",
                artist: "自然之声",
                src: "https://assets.mixkit.co/music/preview/mixkit-driving-ambition-32.mp3",
                cover: "https://images.unsplash.com/photo-1502082553048-f009c37129b9?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80"
            }
        ];
        
        let currentSongIndex = 0;
        let isPlaying = false;
        
        // 初始化鸟类卡片
        function initBirdCards() {
            const birdsContainer = document.querySelector('.birds-container');
            
            birds.forEach(bird => {
                const birdCard = document.createElement('div');
                birdCard.className = 'bird-card';
                
                birdCard.innerHTML = `
                    <img src="${bird.img}" alt="${bird.name}">
                    <div class="bird-name">${bird.name}</div>
                `;
                
                // 添加点击效果
                birdCard.addEventListener('click', function(e) {
                    createClickEffect(e, birdCard);
                    
                    // 随机改变卡片颜色
                    const hue = Math.floor(Math.random() * 60) + 10; // 10-70之间的色调
                    birdCard.style.filter = `hue-rotate(${hue}deg)`;
                    
                    // 1秒后恢复
                    setTimeout(() => {
                        birdCard.style.filter = '';
                    }, 1000);
                    
                    // 播放点击音效
                    playClickSound();
                });
                
                birdsContainer.appendChild(birdCard);
            });
        }
        
        // 创建点击效果
        function createClickEffect(e, element) {
            const rect = element.getBoundingClientRect();
            const x = e.clientX - rect.left;
            const y = e.clientY - rect.top;
            
            const effect = document.createElement('div');
            effect.className = 'click-effect';
            effect.style.left = `${x}px`;
            effect.style.top = `${y}px`;
            
            element.appendChild(effect);
            
            // 动画结束后移除元素
            effect.addEventListener('animationend', () => {
                effect.remove();
            });
        }
        
        // 播放点击音效
        function playClickSound() {
            // 创建一个短暂的点击音效
            const audioContext = new (window.AudioContext || window.webkitAudioContext)();
            const oscillator = audioContext.createOscillator();
            const gainNode = audioContext.createGain();
            
            oscillator.connect(gainNode);
            gainNode.connect(audioContext.destination);
            
            oscillator.frequency.value = 800 + Math.random() * 400;
            oscillator.type = 'sine';
            
            gainNode.gain.setValueAtTime(0.1, audioContext.currentTime);
            gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.3);
            
            oscillator.start(audioContext.currentTime);
            oscillator.stop(audioContext.currentTime + 0.3);
        }
        
        // 初始化播放器
        function initPlayer() {
            // 加载第一首歌
            loadSong(currentSongIndex);
            
            // 播放/暂停按钮事件
            playBtn.addEventListener('click', togglePlay);
            
            // 上一首/下一首按钮事件
            prevBtn.addEventListener('click', prevSong);
            nextBtn.addEventListener('click', nextSong);
            
            // 进度条事件
            progressBar.addEventListener('click', setProgress);
            
            // 音量控制事件
            volumeSlider.addEventListener('input', setVolume);
            
            // 音频事件监听
            audioPlayer.addEventListener('timeupdate', updateProgress);
            audioPlayer.addEventListener('loadedmetadata', updateDuration);
            audioPlayer.addEventListener('ended', nextSong);
            
            // 设置初始音量
            audioPlayer.volume = volumeSlider.value / 100;
            
            // 检查音频链接是否可用
            checkAudioAvailability();
        }
        
        // 检查音频链接是否可用
        function checkAudioAvailability() {
            // 设置超时检查
            setTimeout(() => {
                if (audioPlayer.readyState === 0) {
                    // 如果音频没有加载，尝试使用备选链接
                    console.log('主音乐链接可能不可用，尝试备选链接...');
                    // 这里可以添加备选逻辑
                }
            }, 3000);
        }
        
        // 加载歌曲
        function loadSong(index) {
            const song = songs[index];
            audioPlayer.src = song.src;
            songTitle.textContent = song.title;
            songArtist.textContent = song.artist;
            albumArtImg.src = song.cover;
            
            // 如果正在播放，继续播放新歌曲
            if (isPlaying) {
                audioPlayer.play();
            }
        }
        
        // 切换播放/暂停
        function togglePlay() {
            if (isPlaying) {
                pauseSong();
            } else {
                playSong();
            }
            
            // 添加点击效果
            createClickEffect({clientX: playBtn.getBoundingClientRect().left + 40, 
                              clientY: playBtn.getBoundingClientRect().top + 40}, playBtn);
        }
        
        // 播放歌曲
        function playSong() {
            isPlaying = true;
            audioPlayer.play().then(() => {
                playBtn.innerHTML = '<i class="fas fa-pause"></i>';
                playBtn.style.background = 'linear-gradient(135deg, #9c8363, #7b6b5d)';
            }).catch(error => {
                console.error('播放失败:', error);
                // 如果播放失败，暂停状态
                isPlaying = false;
                playBtn.innerHTML = '<i class="fas fa-play"></i>';
                playBtn.style.background = 'linear-gradient(135deg, #8b7355, #6b5b4d)';
                
                // 显示错误信息
                alert('音乐播放失败，请检查网络连接或尝试刷新页面。');
            });
        }
        
        // 暂停歌曲
        function pauseSong() {
            isPlaying = false;
            audioPlayer.pause();
            playBtn.innerHTML = '<i class="fas fa-play"></i>';
            playBtn.style.background = 'linear-gradient(135deg, #8b7355, #6b5b4d)';
        }
        
        // 上一首歌曲
        function prevSong() {
            currentSongIndex--;
            if (currentSongIndex < 0) {
                currentSongIndex = songs.length - 1;
            }
            loadSong(currentSongIndex);
            playSong();
            
            // 添加点击效果
            createClickEffect({clientX: prevBtn.getBoundingClientRect().left + 30, 
                              clientY: prevBtn.getBoundingClientRect().top + 30}, prevBtn);
        }
        
        // 下一首歌曲
        function nextSong() {
            currentSongIndex++;
            if (currentSongIndex >= songs.length) {
                currentSongIndex = 0;
            }
            loadSong(currentSongIndex);
            playSong();
            
            // 添加点击效果
            createClickEffect({clientX: nextBtn.getBoundingClientRect().left + 30, 
                              clientY: nextBtn.getBoundingClientRect().top + 30}, nextBtn);
        }
        
        // 更新进度条
        function updateProgress() {
            const { currentTime, duration } = audioPlayer;
            
            if (duration) {
                const progressPercent = (currentTime / duration) * 100;
                progress.style.width = `${progressPercent}%`;
                
                // 更新时间显示
                currentTimeEl.textContent = formatTime(currentTime);
            }
        }
        
        // 设置进度
        function setProgress(e) {
            const width = this.clientWidth;
            const clickX = e.offsetX;
            const duration = audioPlayer.duration;
            
            if (duration) {
                audioPlayer.currentTime = (clickX / width) * duration;
            }
        }
        
        // 更新歌曲总时长
        function updateDuration() {
            const duration = audioPlayer.duration;
            if (duration) {
                durationEl.textContent = formatTime(duration);
            }
        }
        
        // 设置音量
        function setVolume() {
            audioPlayer.volume = this.value / 100;
        }
        
        // 格式化时间（秒 -> 分:秒）
        function formatTime(seconds) {
            if (isNaN(seconds)) return '0:00';
            
            const mins = Math.floor(seconds / 60);
            const secs = Math.floor(seconds % 60);
            return `${mins}:${secs < 10 ? '0' : ''}${secs}`;
        }
        
        // 页面加载完成后初始化
        document.addEventListener('DOMContentLoaded', () => {
            initBirdCards();
            initPlayer();
            
            // 为页面添加全局点击效果（除了特定元素）
            document.body.addEventListener('click', function(e) {
                // 排除播放器控制按钮，因为它们已经有自己的效果
                if (!e.target.closest('.control-btn') && !e.target.closest('.bird-card')) {
                    createClickEffect(e, document.body);
                }
            });
            
            // 自动开始播放（带延迟，让用户先看到界面）
            setTimeout(() => {
                if (!isPlaying) {
                    playSong();
                }
            }, 1000);
        });
        
        // 添加键盘控制
        document.addEventListener('keydown', (e) => {
            switch(e.code) {
                case 'Space':
                    e.preventDefault();
                    togglePlay();
                    break;
                case 'ArrowLeft':
                    e.preventDefault();
                    prevSong();
                    break;
                case 'ArrowRight':
                    e.preventDefault();
                    nextSong();
                    break;
                case 'ArrowUp':
                    e.preventDefault();
                    volumeSlider.value = Math.min(100, parseInt(volumeSlider.value) + 10);
                    setVolume.call(volumeSlider);
                    break;
                case 'ArrowDown':
                    e.preventDefault();
                    volumeSlider.value = Math.max(0, parseInt(volumeSlider.value) - 10);
                    setVolume.call(volumeSlider);
                    break;
            }
        });
        
        // 添加一个简单的离线检测
        window.addEventListener('online', function() {
            console.log('网络已连接');
        });
        
        window.addEventListener('offline', function() {
            console.log('网络已断开');
            alert('网络连接已断开，音乐播放可能受到影响。');
        });
    </script>
</body>
</html>
