Rise Evade - Music catalog (kendi repo'nuza yukleyin)
=================================================

    MusicRepo/
      catalog.lua              <- tek kaynak (BASE satirini kendi raw adresinizle degistirin)
      music/part1/  part2/  part3/   <- 260 mp3 (944 MB) 3 parcaya bolundu
      covers/part1/  part2/          <- 218 kapak gorseli (22 MB)

Neden 3 parca: GitHub'a 100'er 100 dosya yukleyebilmen icin mp3'ler parcalara bolundu.
Bir klasoru yuklerken digerlerini de ayni repoya ekle (iskeleti koru).

Adimlar
--------
1. catalog.lua dosyasini ac ve su satiri kendi repo'na gore degistir:
       local BASE = "https://raw.githubusercontent.com/<SENIN-KULLANICI>/<REPO>/main"

2. music/part1, music/part2, music/part3 ve covers/part1, covers/part2 klasorlerini
   repo'na yukley. Toplam ~966 MB -> Git LFS gerekebilir:
       *.mp3 filter=lfs diff=lfs merge=lfs -text

3. Rise Evade tarafinda tek satiri guncelle (music_player.luau):
       Music.CatalogURL = "https://raw.githubusercontent.com/<SENIN-KULLANICI>/<REPO>/main/catalog.lua"

Katalog formati
---------------
    Name, Artist, Duration ("mm:ss"),
    Cover = "rbxassetid://..."              (varsa dogrudan gosterilir)
    CoverURL = BASE.."/covers/partN/xxx"   (asset yoksa indirilir + RiseEvade/music/ icine cache'lenir)
    AudioURL = BASE.."/music/partN/xxx.mp3"  (zorunlu)
    CacheName = "xxx.mp3"                  (cache dosya adi)

Gereksinimler
-------------
* AudioURL verilmeyen kayitlar listede gosterilmez.
* Ses dosyalari once indirilip executor'in RiseEvade/music/ klasorune cache'lenir.
