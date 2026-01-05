<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Коран — Чистый Текст</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700&family=Amiri:wght@400;700&display=swap" rel="stylesheet">
    <style>
        :root { --bg: #ffffff; --header: #fbfbfb; --gold: #b2904f; --line: #f0f0f0; }
        * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
        body { background: var(--bg); font-family: 'Montserrat', sans-serif; margin: 0; padding: 0; }
        
        .main-header { position: sticky; top: 0; z-index: 1000; background: var(--header); padding: 15px 0; border-bottom: 1px solid var(--line); display: flex; flex-direction: column; align-items: center; }
        .main-header h1 { font-size: 18px; margin: 0 0 10px 0; font-weight: 700; }
        .search-container { width: 90%; }
        #surahSearch { width: 100%; padding: 12px 15px; border-radius: 12px; border: 1px solid var(--line); background: #f0f0f0; outline: none; border:none; }

        .surah-list { width: 100%; display: flex; flex-direction: column; }
        .surah-item { display: flex; align-items: center; padding: 18px 20px; border-bottom: 1px solid var(--line); cursor: pointer; }
        .surah-item:active { background: #f5f5f5; }
        .surah-num { color: var(--gold); font-size: 14px; width: 45px; font-weight: bold; }
        .surah-info { flex-grow: 1; }
        .surah-name-ru { font-size: 16px; font-weight: 600; }
        .surah-name-ar { font-size: 24px; color: var(--gold); font-family: 'Amiri', serif; }

        .surah-content { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: var(--bg); z-index: 2000; overflow-y: auto; }
        .surah-header { position: sticky; top: 0; z-index: 2001; background: var(--header); height: 60px; display: flex; align-items: center; padding: 0 20px; border-bottom: 1px solid var(--line); }
        .back-btn { font-size: 32px; color: var(--gold); cursor: pointer; margin-right: 15px; }
        
        .basmala-header { text-align: center; font-family: 'Amiri', serif; font-size: 32px; padding: 30px 10px; color: var(--gold); border-bottom: 1px solid var(--line); line-height: 1.5; }
        .ayah-box { padding: 25px 20px; border-bottom: 1px solid var(--line); }
        .arabic { direction: rtl; font-family: 'Amiri', serif; font-size: 34px; line-height: 2.2; text-align: right; margin-bottom: 15px; color: #000; }
        .translation { font-size: 17px; line-height: 1.6; color: #333; margin-bottom: 20px; }
        
        .audio-btn { background: var(--gold); border: none; color: #fff; padding: 12px 20px; border-radius: 12px; font-weight: 600; cursor: pointer; transition: 0.2s; display: flex; align-items: center; gap: 8px; font-family: 'Montserrat', sans-serif; }
        .audio-btn:active { transform: scale(0.95); }
        .audio-btn.playing { background: #27ae60; }
    </style>
</head>
<body>

<div class="main-header">
    <h1>Al-Qur’an</h1>
    <div class="search-container"><input type="text" id="surahSearch" placeholder="Поиск суры..." onkeyup="filterSurahs()"></div>
</div>

<div class="surah-list" id="surahList"></div>

<div id="surahWindow" class="surah-content">
    <div class="surah-header">
        <div class="back-btn" onclick="closeSurah()">‹</div>
        <h1 id="windowTitle" style="font-size:16px; flex-grow:1; text-align:center; margin:0; font-weight:700;"></h1>
        <div style="width:30px;"></div>
    </div>
    <div id="windowContainer"></div>
</div>

<script>
const surahNamesRu = {
    1:"Аль-Фатиха", 2:"Аль-Бакара", 3:"Аль-Имран", 4:"Ан-Ниса", 5:"Аль-Маида", 
    6:"Аль-Анам", 7:"Аль-Араф", 8:"Аль-Анфаль", 9:"Ат-Тауба", 10:"Юнус"
};

let allSurahs = [];

async function initApp() {
    try {
        const res = await fetch("https://api.alquran.cloud/v1/surah");
        const data = await res.json();
        allSurahs = data.data;
        renderSurahs(allSurahs);
    } catch (e) { console.log(e); }
}

function renderSurahs(data) {
    const list = document.getElementById('surahList');
    list.innerHTML = data.map(s => `
        <div class="surah-item" onclick="openSurah(${s.number}, '${surahNamesRu[s.number] || s.englishName}')">
            <div class="surah-num">${s.number}</div>
            <div class="surah-info"><span class="surah-name-ru">${surahNamesRu[s.number] || s.englishName}</span></div>
            <div class="surah-name-ar">${s.name}</div>
        </div>
    `).join('');
}

async function openSurah(id, name) {
    const win = document.getElementById('surahWindow');
    const container = document.getElementById('windowContainer');
    document.getElementById('windowTitle').innerText = name;
    win.style.display = 'block';
    container.innerHTML = "<p style='text-align:center; padding:50px;'>Загрузка...</p>";

    try {
        const res = await fetch(`https://api.alquran.cloud/v1/surah/${id}/editions/quran-uthmani,ru.kuliev`);
        const data = await res.json();
        const arabicData = data.data[0].ayahs;
        const kulievData = data.data[1].ayahs;

        const basmalaText = "بِسْمِ اللَّهِ الرَّحْمَنِ الرَّحِيمِ";
        let html = "";

        if (id !== 1 && id !== 9) {
            html += `<div class="basmala-header">${basmalaText}</div>`;
        }

        html += arabicData.map((ayah, i) => {
            let text = ayah.text;
            
            if (i === 0 && id !== 1 && id !== 9) {
                // НОВЫЙ МЕТОД: Разбиваем аят на слова.
                // Басмала в шрифте Uthmani — это всегда первые 4 слова.
                // Мы их просто выбрасываем.
                let words = text.split(" ");
                if (words.length > 4) {
                    text = words.slice(4).join(" ");
                }
            }

            return `
                <div class="ayah-box">
                    <div class="arabic">${text}</div>
                    <div class="translation">${kulievData[i].text}</div>
                    <button class="audio-btn" onclick="playAudio('https://cdn.islamic.network/quran/audio/128/ar.alafasy/${ayah.number}.mp3', this)">
                        ▶ Слушать
                    </button>
                </div>`;
        }).join('');

        container.innerHTML = html;
        container.scrollTop = 0;
    } catch (e) { container.innerHTML = "Ошибка"; }
}

function playAudio(url, btn) {
    if (window.quranPlayer) {
        window.quranPlayer.pause();
        if (window.lastBtn) { window.lastBtn.classList.remove('playing'); window.lastBtn.innerText = "▶ Слушать"; }
    }
    window.quranPlayer = new Audio(url);
    window.lastBtn = btn;
    btn.classList.add('playing');
    btn.innerText = "🔊 Играет...";
    window.quranPlayer.play();
    window.quranPlayer.onended = () => { btn.classList.remove('playing'); btn.innerText = "▶ Слушать"; };
}

function closeSurah() { 
    document.getElementById('surahWindow').style.display = 'none'; 
    if (window.quranPlayer) window.quranPlayer.pause(); 
}

function filterSurahs() {
    const q = document.getElementById('surahSearch').value.toLowerCase();
    const filtered = allSurahs.filter(s => {
        const name = (surahNamesRu[s.number] || s.englishName).toLowerCase();
        return name.includes(q) || s.number.toString() === q;
    });
    renderSurahs(filtered);
}

window.onload = initApp;
</script>
</body>
</html>
