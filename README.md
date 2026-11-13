Rise Evade - Music catalog (kendi repo'nuza yukleyin)
=================================================

    MusicRepo/
      catalog.lua                 <- tek kaynak (BASE satirini kendi raw adresinizle degistirin)
      music/part1/ part2/ part3/  <- 260 mp3 (944 MB) 3 parcaya bolundu
      covers/part1/ part2/         <- 218 kapak gorseli (22 MB)

GitHub'a yukleme (WEB ARAYUZUNDE 100 DOSYADAN FAZLASI OLMAZ)
-----------------------------------------------------------
Bu klasor git repo olarak hazirlandi (branch: main, 1 commit).
Sadece su iki komutu calistir:

    cd "C:\Users\delik\Downloads\Rise Evade\MusicRepo"
    git remote add origin https://github.com/<SENIN-KULLANICI>/<REPO>.git
    git push -u origin main

Git Credential Manager acilip tarayicida GitHub'a giris yapman isteyecektir.
(Tek seferlik PAT da kullanabilirsin: https://github.com/settings/tokens)

Not: toplam ~950 MB. GitHub "1 GB altinda olsun" diye onerir ama tek dosya
siniri 100 MB (en buyuk mp3 15 MB) sorun degil, web arayuzu dosya sayisi
sinirindan dolayi reddediyor. git push ile tek seferde gider.

Web arayuzu kullanmak istersen: part1/part2/part3 klasorlerini tek tek, her
seferde en fazla 20-25 dosya secerek yukle.

Repo'ya girdikten sonra iki yeri guncelle
---------------------------------------
1) catalog.lua:
       local BASE = "https://raw.githubusercontent.com/<SENIN-KULLANICI>/<REPO>/main"
   (dosyayi repoda degistirip tekrar commit + push et)

2) Rise Evade tarafinda (music_player.luau):
       Music.CatalogURL = "https://raw.githubusercontent.com/<SENIN-KULLANICI>/<REPO>/main/catalog.lua"

Katalog formati
---------------
    Name, Artist, Duration ("mm:ss"),
    Cover = "rbxassetid://..."                (varsa dogrudan gosterilir)
    CoverURL = BASE.."/covers/partN/xxx"     (asset yoksa indirilir + RiseEvade/music/ icine cache'lenir)
    AudioURL = BASE.."/music/partN/xxx.mp3"   (zorunlu)
    CacheName = "xxx.mp3"                    (cache dosya adi)

Gereksinimler
-------------
* AudioURL verilmeyen kayitlar listede gosterilmez.
* Ses dosyalari once indirilip executor'in RiseEvade/music/ klasorune cache'lenir.
