---
name: rnd-execution
description: Evidence-gated R&D execution for agent-led research work.
version: 0.2.0
author: Abdulbaki (TopcuAbdulbaki), Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [Research, Experiments, Methodology, Documentation]
    related_skills: [grounded-citations]
---

# R&D Execution Skill

Proje-agnostik arastirma-gelistirme yurutme disiplini: kanit kapili, tek-degiskenli,
kaydi duzgun. Proje bilgisi (yollar, veri, kararlar) projenin kendi dokumanlarinda
kalis; bu skill YALNIZ yontemdir.

## When to Use
- Deney/arastirma programi yuruturken (hipotez -> deney -> olcum -> karar)
- Mekanizma tasarlayip kilitleyecegin islerde; karsilastirmali benchmark'larda
- "Su karar bozuldu, neye dokunmali?" durumlarinda (mutasyon fisi)
- Don't use: tek seferlik betik/arac isi, olcusuz urun ozelligi gelistirme

## Kaideler (7)
1. ONCE KONUS, SONRA INSA: tasarim/esik/veri/protokol secimini sessizce yapma;
   somut oner (dosya/sayi duzeyinde) + SEZGI (neden calismali) + uzlasi.
2. TEK DEGISEN: sonuc atfedilebilsin; birlikte gitmek zorundaysa etiket "birlesik".
3. ADALETLI KIYAS: ayni kosullar, eslesmis butce (hangi butce oldugunu yaz),
   kilitli varsayilanlar acik; adalet saglanamiyorsa "henuz kiyaslanamaz" de, sayi verme.
4. OLc, CIKARMA YAPMA: her iddia kaynak etiketiyle — (olculdu / koddan okundu /
   hatirlaniyor) — ve ikinci bakisla (kontrol kosusu / baska seed / mikro test).
   HARICI kaynak iddialari (web/literatur) icin `grounded-citations` skill'i
   kullan (opsiyonel): uretilmis [n] atiflari + Sources blogu + verbatim kanit
   kapisi; onun '[unverified]' damgasi bizim 'hatirlaniyor' etiketimizin
   karsiligir. Kurulu degilse ayni disiplini elle uygula: kaynagi GETIRDIGIN
   anda kaydet, uydurma numara yok, Sources listesini elle yazma.
5. KAYIT: sayisal sonuc kalici sonuc arsivinde; "yazildi ama hic kosulmadan" AYRI
   kategori; ureten script repoda yasar, yeri yoksa kayit NOT-LANDED damgasi +
   script yolu ile tutulur.
6. CELISKIYI RAPORLA: dokuman/kod carsarsa once kodu dogrula, soyle, onayla duzelt.
7. COST GATE: uzun kosudan once "hangi karari degistirecek" + sure tahmini; cevap
   yoksa kosturma.

## Gurultu tabani ve donma
- Baslik iddiasi >=3 tohum (mean + min-max); tek tohum = yonlendirici, iddia degil.
- Kilidi bozma: mikro testle kilitleyen varsayilan sessizce degistirilemez;
   off-switch + bilincli ablation (etiketli kosu) sart.
- DONDUR: olculen mekanizma sayi gelene kadar degismez; yeniden tasarim sayidan SONRA.

## Karar defteri + MUTASYON FISI (karar bozulunca)
- Her kilidli kararin KARTI: deger, gerekce, kanit imi, BAGIMLILAR (kod/config/test/
  sonuc/dokuman) + revizyonlar. Elle tutulur, lint dogrular (bagim yollari var mi,
  kartsiz karar kalmis mi). Kayit deposuna yazmadan ONCE mevcut girdiyi taze oku;
  eslesme anahtarini kopyala-yapistir yap (hatirlama ile yazma), islem sonrasi geri oku.
- Karar bozulunca FIS ac: (a) bagimli listesi + degerin literal aramasi (kayit
  disi bagim avina karsi tamamlayici), (b) her satir: KIRILIR (onarim+regresyon testi) /
  YENIDEN-TEST (kirlenen kosu listeye) / ETIKETLE (eski sonuc `superseded: <fis>`
  damgasiyla YERINDE kalir, silinmez) / DOKUNULMAZ, (c) BILESIK ETKILER: ikinci
  dereceden turetilmis cikarimlar da fise girer, (d) kart'a revisions + ust duzey
  uyari, (e) kapanis olcutu: DOKUNULMAZ disi her satir islenmis.
- Fis kalici kayittir (fisler klasoru); bir sonraki oturum fisten devam eder.

## Oturum rituali ve dokuman hijyeni
- Acilis: durum + canli el kitabini oku, durumu 5 satirda geri soyle, onayla gir.
- Kapanis: el kitabina APPEND; is kapandiysa SINDIR-TEMIZLE — kayitlar dogru
  evlerine islenir (sonuc arsivi / tarih kaydi / fikir defteri / fis) ve el
  kitabindan SILINIR: tek el kitabi, copluk yok.
- Her cevabin sonuna numarali ACIK SORULAR; ertelenen satir oraya duser.
- Geri donulmez is oncesi SES CIKAR (silme / uzerine yazma / uzun kosu).
- Yan isleri (paylasim/dagitim/lojistik) SONA otele; ana akista dallanma — kullanici
  acikca istemedikce yeni cabuk acma. Ozgun ajan-hilesi (kilit, orkestrasyon) ilk
  gorundugunde 3-4 satirda ne oldugunu acikla; gizemli davranis istenmez.
- VERBATIM kayitlar (konusma dokumu, karar alintilari) DOKUNULMAZ; yonlendirme
  yalniz yasayan dokumanlarda guncellenir.

## Pitfalls
- Gecici dizine (/tmp vb.) kanit baglama: kaybolur (yasanmis kayip). Sonuc arsivi kalici.
- Kopya dosya tutma: kopya curur ve yanlis yonlendirir — tek kaynak + uretilmis gorunum.
- Boru hatti/ozet komutlari cikis kodunu yutar (pipefail); olcumu islem ONCESI/SONRASI
  sirasina dikkat (render sonrasi boyut olc). COMMIT KAPISI: dogrulama/lint gercek
  exit==0 degilse commit satiri CALISMAZ — kirmiziyken gecen commit kayitlarin
  guvenilirligini silar.
- YAZMA KILIDI: parcali dosya islerinde TUM dogrulamalari (kapsam, siniflandirma,
  kayip-esitlik TEK birimde) yazmadan once calistir; uyusmazlikta hicbir dosya
  dokunulmamali (assert'ler yazma adimindan once). Boylece hatali bolme/islem dosyayi
  bozamaz; tek satir duzeltip yeniden kosulur.
- Yol degistiren islem (tasima/yeniden adlandirma/silme) ile o yola yazma AYNI anda
  yapilamaz: yazma eski yolu hedefler ve sessizce duser. Adimlari siraya bagla;
  bagimli isleri tek yigitta paralellestirme.
- `git rm` yol listesinde TEK izsiz yolda butun komutu iptal eder; izlenmeyeni dogrudan
  sil, izleneni git'le. Ignore'lu bir dizinde calisiyorsan izleme durumunu once
  `ls-files`/`check-ignore` ile olc.
- Olcum birimi karistirma (satir / newline / bayt) — karsilastirmayi TEK birimle yap.
- Test dosyasi fixture'ini kendi assert'inden ayri yaz; cakismayi kod yazmadan sur.

## Verification
- Kayit butunlugu lint'i yesil (manifest<->dosya, baglantilar, butce kapilari).
- KAPAK TESTI: sifir baglamli taze ajan, protokol + kisa soru listesiyle dogru cevabi
  <=N dosyada bulabiliyor mu? Bulamiyorsa yonlendirme bozuktur, duzelt ve tekrarla.
  Sorular TEK cevapli olsun: kaynak/donem adini soruda sabitle (ayni gunun iki ayri
  turu varsa hangisi) — belirsiz soru sinavi kirletir. Ayni sinavi IKI bagimsiz
  taze ajandan gecir: kabul = 2/2 (tek gecis sans olabilir, determinizm degil).
- Kaynak etiketi denetimi: butun iddialar (olculdu / koddan okundu / hatirlaniyor)
  etiketi tasiyor; etiketsiz iddia kalmadi.