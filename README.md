# RANK-SYSTEM
QBCORE AND QBOX
FLOW PLAYER BARU
----------------
1. Player baru = GUIDEME sahaja.
2. GUIDEME sentiasa nampak atas kepala tanpa tekan Z.
3. Selagi GUIDEME, XP tidak bergerak dan icon lain tidak boleh override.
4. Staff/Admin: /guidereset [ID]
   -> GUIDEME tamat
   -> XP reset 0
   -> icon jadi newplayer
   -> progression XP bermula.

AUTO RANK XP
------------
Auto rank hanya:
newplayer -> penrantis 1 -> penrantis  2 -> penrantis  3 -> penrantis 4 -> perkasa 5

PERKASA 5 ialah MAX auto rank. Semua icon selepas itu tidak boleh diperoleh melalui XP.

OWNED ICON SYSTEM
-----------------
Staff/admin beri hak icon menggunakan:
/rankicon [ID] [NAMA ICON]

Contoh:
/rankicon 12 medic
/rankicon 12 kerabat 1
/rankicon 12 topdonator5

Setiap icon yang diberi disimpan sebagai OWNED ICON. Memberi icon baru TIDAK membuang icon lama.
Player boleh memiliki banyak icon dan tukar-tukar sendiri.

PLAYER TUKAR ICON
-----------------
Buka:
/rank -> My Icons
atau shortcut:
/myicons

Dalam My Icons:
- pilih mana-mana icon yang player sudah miliki untuk aktifkan.
- pilih "Auto Rank / Balik" untuk tutup manual icon dan kembali ke rank XP semasa.

PENTING:
"Auto Rank / Balik" TIDAK membuang ownership. Player masih boleh pilih icon itu semula kemudian.

STAFF BUANG ICON
----------------
/rankiconremove [ID] [NAMA ICON]
Contoh:
/rankiconremove 12 medic

Ini buang HAK icon medic dari player. Jika medic sedang aktif, player terus kembali ke Auto Rank.

/rankiconremove [ID]
Tanpa nama icon hanya tutup icon aktif dan kembali ke Auto Rank; ownership semua icon masih kekal.

DATABASE
--------
Resource auto-create table:
ranksystem_owned_icons

Jadi semua icon yang player pernah dapat kekal selepas reconnect/restart server.
Icon manual lama dari build sebelumnya akan auto-migrate masuk ke owned icons.

PERMISSION
----------
Default staff permission:
mod, admin, god

PAPARAN ICON
------------
- GUIDEME: sentiasa visible.
- Semua icon lain: visible semasa hold Z.

RANK INFO CUSTOM PNG
--------------------
Muka 1: html/rankinfo_page1.png
Muka 2: html/rankinfo_page2.png

Anda boleh replace dua fail PNG ini dengan gambar sendiri (apa-apa dimensi/aspect ratio).
Kekalkan nama fail tepat seperti di atas, kemudian jalankan: restart ranksystem
Rank Info akan cache-bust/reload gambar terbaru setiap kali dibuka.
