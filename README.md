# RANK-SYSTEM
QBCORE AND QBOX
RANKSYSTEM V4 - PANDUAN MUDAH (BM)
================================

APA YANG SCRIPT INI BUAT?
- Player baru bermula dengan status GUIDEME.
- Selagi GUIDEME, icon guide sentiasa nampak dan XP belum berjalan.
- Admin perlu tamatkan guide. Selepas itu rank menjadi newplayer, XP = 0.
- Icon GUIDEME yang sentiasa nampak akan hilang. Icon rank biasa muncul apabila tekan dan tahan Z.
- XP auto bertambah mengikut tetapan config.lua (asal: setiap 30 minit).

2. HILANGKAN GUIDEME
-------------------
Dalam CHAT GAME (admin):
    /guidecomplete 1

Dalam SERVER CONSOLE / txAdmin (TANPA /):
    guidecomplete 1

PENTING: Tukar 1 kepada server ID SEMASA player yang hendak diselesaikan guide.
Untuk tamatkan guide diri sendiri dalam game, boleh cuba /guidecomplete
(jika masih terima ralat ID, gunakan /guidecomplete [ID] yang tepat).

Selepas berjaya:
- Rank: newplayer
- XP: 0
- Icon GUIDEME yang sentiasa terlihat akan hilang.
- Tekan dan tahan Z untuk melihat icon rank biasa.

Jika nak tamatkan guide DAN reset XP kepada 0 sekali lagi:
Dalam game: /guidereset 1
Di server console: guidereset 1
NOTA: guidereset BUKAN arahan untuk kembalikan status GUIDEME.

3. SEMAK KALAU GUIDEME MASIH ADA
--------------------------------
Dalam CHAT GAME (admin): /rankdebug 1
Dalam SERVER CONSOLE: rankdebug 1

Lihat txAdmin Live Console, cari baris yang bermula dengan [ranksystem].
Semakan yang dijangka: guide_completed=true atau 1, xp=0.
Jika selepas guidecomplete rank masih GUIDEME:
- Pastikan ID player betul dan pemain sudah siap loading.
- Pastikan tiada DUA folder/resource ranksystem yang berjalan.
- Pastikan oxmysql disambung ke database yang BETUL.
- Cuba restart ranksystem, kemudian keluar/masuk semula karakter.
- Ambil screenshot baris [ranksystem] GUIDE VERIFY FAILED atau ralat SQL
  daripada SERVER CONSOLE, bukan gambar notifikasi sahaja.
Jangan kongsi password database.

Nota fix V4: sesetengah versi oxmysql pulangkan guide_completed sebagai
boolean true, bukan nombor 1. V4 menerima kedua-dua bentuk. Ralat V3
'saved=true xp=0' sepatutnya tidak lagi dianggap gagal oleh semakan V4.

4. COMMAND UTAMA
----------------
Dalam chat game, letak / di hadapan. Dalam txAdmin console, BUANG /.

/rank                     Buka menu rank.
/myicons                  Pilih icon yang player sudah miliki.
/guidecomplete [ID]       Admin: tamatkan GUIDEME, mula newplayer/0 XP.
/guidereset [ID]          Admin: tamatkan guide & reset newplayer/0 XP.
/rankdebug [ID]           Semak rekod guide, lihat output server console.
/rankicon [ID] [NAMA]     Staff: beri dan aktifkan icon, contoh /rankicon 1 medic.
/rankiconremove [ID] [NAMA]  Staff: buang hak icon tertentu.
/rankiconremove [ID]      Staff: matikan icon manual, balik auto rank.
/rankaddxp [ID] [JUMLAH]  Admin: tambah XP selepas guide selesai.
/ranksetxp [ID] [JUMLAH]  Admin: tetapkan XP selepas guide selesai.

5. MACAM MANA ICON BERFUNGSI?
----------------------------
- GUIDEME: sentiasa kelihatan selagi guide belum selesai.
- Icon rank biasa: hanya terlihat apabila tahan Z.
- /myicons: pilih icon yang admin beri atau pilih Auto Rank / Balik.
- Icon yang player sudah miliki kekal, walaupun bertukar kepada Auto Rank.
- Auto rank maksimum dalam config asal: perkasa 5.

6. NAK TUKAR GAMBAR RANK INFO?
-----------------------------
Gantikan file gambar dalam folder html ini (NAMA MESTI SAMA):
    html/rankinfo_page1.png
    html/rankinfo_page2.png
Kemudian jalankan: restart ranksystem

PENTING: Kotak 'Rank: guideme' dalam screenshot ialah menu ox_lib,
BUKAN gambar PNG di atas. Tulisan kotak itu datang daripada
client/client.lua (function showRankMenu). Warna gelap menu mungkin
berasal daripada tema ox_lib; menukar PNG tidak mengubah kotak menu.

7. DATABASE
-----------
Script menggunakan table ranksystem_players dan menyimpan rekod mengikut
citizenid KARAKTER, bukan server ID tetap. Jangan jalankan SQL reset pada
semua player semata-mata untuk hilangkan GUIDEME seorang player.
Jika perlu semak secara manual, dalam phpMyAdmin/HeidiSQL jalankan:

    SELECT citizenid, guide_completed, xp
    FROM ranksystem_players
    WHERE citizenid = 'CITIZENID_KARAKTER';

Selepas guide tamat, guide_completed sepatutnya 1 dan xp 0.


NOTA: V4 dibaiki berdasarkan log oxmysql yang diberi. Ujian sebenar
memerlukan server FiveM anda; panduan ini bukan jaminan ia telah diuji di server anda.
