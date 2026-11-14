Rise Evade - Music catalog
==========================

Bu repo Rise Evade script'inin muzik listesini ve dosyalarini barindirir.
Artik Yin Yang reposuna hicbir bagimlilik yoktur.

    catalog.lua                  -> tek kaynak (422 sarki, alfabetik sirali)
    music/part1 ... part6       -> 422 mp3 (~1.29 GB)
    covers/part1 ... part5      -> 380 kapak gorseli

Katalogda BASE satiri zaten kendi adresimize ayarli:
    local BASE = "https://raw.githubusercontent.com/realdausita/Rise-Music/main"

Script tarafinda:
    Music.CatalogURL = "https://raw.githubusercontent.com/realdausita/Rise-Music/main/catalog.lua"
    (Rise Evade/music_player.luau)

Guncelleme yapmak icin:
    git add -A
    git commit -m "guncelleme"
    git push origin main

Katalog formati
---------------
    Name, Artist, Duration ("mm:ss"),
    Cover = "rbxassetid://..."                (varsa dogrudan gosterilir)
    CoverURL = BASE.."/covers/partN/xxx"     (asset yoksa indirilir + cache'lenir)
    AudioURL = BASE.."/music/partN/xxx.mp3"   (zorunlu)
    CacheName = "xxx.mp3"                    (cache dosya adi)

Sanatcilar
----------
    Swirf (46) | Deha Inc. (26) | Killoki (60) | Qimp (30)
    Bu 162 sarki YouTube'dan (yt-dlp + ffmpeg) indirildi, mp3 128kbps + kapak
    ile eklendi. Kaynak kanallar: SWIRF (UCBfrUzLfk_CCOz6uJHQvcSQ),
    swirf (UCHlrzfLA5sMGkSXQTQtmmOQ), DEHA INC. (UCmVbkpXLxPCz5dEpMRVF7fw),
    13 Killoki - Topic (UCXkqA4ga8HyduyCaeCYSwJQ), KILLOKI (UCh4xtpUxKKodverMV0g-EAQ),
    Qimp Vault - Topic (UCSAaOMLvsEj2wZ-xEXdZAdQ), qimptoven (UCi4TJYdUiZzwe5xlW6RC-Ug)

Notlar
------
* AudioURL verilmeyen kayitlar listede gosterilmez.
* Oyuncu ses dosyalarini ilk calismada indirip executor'in RiseEvade/music/ klasorune cache'ler.
* GitHub web arayuzu tek seferde 100 dosyadan fazlasini kabul etmiyor; bu yuzden
  mp3'ler parcalara bolundu (her part <= 100 dosya).
