Rise Evade - Music catalog
==========================

Bu repo Rise Evade script'inin müzik listesini ve dosyalarini barindirir.
Artik Yin Yang reposuna hicbir bagimlilik yoktur.

    catalog.lua                 -> tek kaynak (260 sarki)
    music/part1/ part2/ part3/  -> 260 mp3 (944 MB)
    covers/part1/ part2/        -> 218 kapak gorseli (asset olmayanlar, 22 MB)

Katalogda BASE satiri zaten kendi adresimize ayarli:
    local BASE = "https://raw.githubusercontent.com/realdausita/Rise-Music/main"

Script tarafinda:
    Music.CatalogURL = "https://raw.githubusercontent.com/realdausita/Rise-Music/main/catalog.lua"
    (Rise Evade/music_player.luzu)

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

Notlar
------
* AudioURL verilmeyen kayitlar listede gosterilmez.
* Oyuncu ses dosyalarini ilk calismada indirip executor'in RiseEvade/music/ klasorune cache'ler.
* GitHub web arayuzu tek seferde 100 dosyadan fazlasini kabul etmiyor; bu yuzden
  mp3'ler 3 parcaya bolundu (87/87/86).
