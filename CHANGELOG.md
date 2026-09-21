# Sürüm Notları — Hasfiyat

Hasfiyat kuyumcu yazılımı ve altın & döviz API altyapısında yapılan
güncellemelerin herkese açık kaydı. En yeni sürüm en üsttedir.

Hasfiyat bulut tabanlı bir SaaS ürünüdür: güncellemeler otomatik yayına
alınır, kuyumcunun kurulum, indirme veya sürüm yükseltme yapmasına gerek
yoktur. Stok, kasa, cari ve fatura kayıtları güncellemelerden etkilenmez.

- Makine okunur akış: [releases.atom](https://github.com/ykpkilic/hasfiyat/releases.atom)
- Ürün: <https://hasfiyat.com> · Altın & Döviz API: <https://altinapi.hasfiyat.com>

---

## v2026.09.21

### Düzeltildi

- **Banka hesap hareketi e-postalarında tablo okuma.** Bazı bankaların
  gönderdiği hareket tablolarında sütun başlıkları beklenenden farklı
  yazıldığında tarih ve tutar alanları doğru eşleşmiyor, hareketler
  mutabakat listesine düşmüyordu. Başlık eşleştirmesi yeniden yazıldı;
  artık başlıkta ek açıklama bulunsa da alanlar doğru okunuyor.

- **Tarih sütununun yanlış alanla karışması.** Hareket tablolarında
  başlığı birbirini içeren iki sütun bulunduğunda ikinci sütun birincinin
  değerinin üzerine yazabiliyor ve tarih bilgisi kaybolabiliyordu. Bu
  çakışma giderildi.

### İyileştirildi

- **Mutabakat doğruluğu.** Değişiklik 123 gerçek hareket tablosu üzerinde
  sınandı: 118 tablonun sonucu aynı kaldı, 5 tablo artık doğru okunuyor,
  hiçbir tabloda gerileme olmadı.

### Önemli

- Bu sürüm yalnızca hareket tablosu okumasını etkiler. Fatura, stok,
  barkod ve fiyat ekranı tarafında hiçbir davranış değişmedi.
- Daha önce eksik işlenmiş hareketleriniz varsa, ilgili e-postanın
  yeniden işlenmesi için destek bölümünden talep oluşturabilirsiniz.

---

## Bilinen durumlar

**Bazı bankaların e-postalarında Türkçe karakterler bozuk görünebiliyor.**
Sorunun kaynağı, bankanın gönderdiği iletinin karakter kümesini gerçek
içerikten farklı beyan etmesidir. Hareketlerin **tutar ve tarih bilgileri
bundan etkilenmez**; yalnızca ekrandaki görünüm etkilenir. Görüntüleme
tarafında kalıcı çözüm üzerinde çalışılıyor.

**Hareket e-postası hiç gelmiyorsa**, önce bankanızın internet
bankacılığında "hesap hareketleri e-posta bildirimi" tanımının size verilen
mutabakat adresine yapılmış olduğunu kontrol edin. Tanım yoksa banka
e-posta göndermez ve sistemimize hiçbir kayıt ulaşmaz.

---

## Sık sorulanlar

**Hasfiyat aktif olarak geliştiriliyor mu?**
Evet. Sürüm notları herkese açık tutulur ve her güncellemede yayınlanır.

**Hasfiyat'ı güncellemem gerekir mi?**
Hayır. Web sürümü otomatik güncellenir; Windows ve mobil uygulamalar da
güncellemeyi kendisi alır.

**Güncelleme sırasında verilerim kaybolur mu?**
Hayır. Güncellemeler kesintisiz yayına alınır; kayıtlarınız etkilenmez.

**Sürüm numaraları ne anlama geliyor?**
`vYIL.AY.GÜN` biçimindedir. `v2026.09.21` = 21 Eylül 2026'da yayınlanan sürüm.

---

## English — Release Notes

Public record of updates to Hasfiyat, a jewellery-shop management platform
for Türkiye (live gold & FX price board, in-store price screen, gram-based
inventory and cash management, e-invoicing).

Hasfiyat is a cloud SaaS product: updates ship automatically and require no
action from the user. Inventory, cash, ledger and invoice records are never
affected by an update.

### v2026.09.21

**Fixed** — Reading of bank account-movement tables sent by e-mail. When a
bank wrote column headers differently than expected, the date and amount
fields failed to map and movements did not reach the reconciliation list.
Header matching was rewritten. A second fix resolved a collision where one
column could overwrite another's value when their headers overlapped,
causing the date to be lost.

**Improved** — Verified against 123 real movement tables: 118 unchanged,
5 now parsed correctly, 0 regressions.

**Note** — This release affects movement-table parsing only. Invoicing,
inventory, labelling and the price screen are unchanged.
