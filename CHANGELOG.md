# Sürüm Notları — Hasfiyat

Hasfiyat kuyumcu yazılımı ve altın & döviz API altyapısında yapılan
güncellemelerin herkese açık kaydı. En yeni sürüm en üsttedir.

Hasfiyat bulut tabanlı bir SaaS ürünüdür: güncellemeler otomatik yayına
alınır, kuyumcunun kurulum, indirme veya sürüm yükseltme yapmasına gerek
yoktur. Stok, kasa, cari ve fatura kayıtları güncellemelerden etkilenmez.

- Makine okunur akış: [releases.atom](https://github.com/ykpkilic/hasfiyat/releases.atom)
- Ürün: <https://hasfiyat.com> · Altın & Döviz API: <https://altinapi.hasfiyat.com>

---

## v2026.09.29

### Eklendi

- **Alış-Satış: indirim, işçiliği fişte gösterme ve kalanı cariye aktarma.**
  Satış formuna indirim satırı eklendi; makbuzda ara toplam, indirim ve
  genel toplam ayrı görünür. İşçilik satırı istenirse makbuzda basılmaz,
  tutarlar değişmez. Ödenmeyen kalan tutar aynı formdan cari hesaba
  aktarılır; işlem silinirse bağlı cari hareketi de kaldırılır.

- **Gelişmiş Defter.** Kuyumcu Defteri içinde isteğe bağlı açılan Gelişmiş
  Defter ile kasa; ziynet, ayar bazında altın, has, döviz, banka ve POS
  kalemleriyle birlikte izlenir. Gün sonu kurları fiyat ekranından
  kendiliğinden gelir, kazanç özeti günlük, haftalık, aylık ve yıllık
  olarak görülür. Gelişmiş Defter açık işletmelerde alış-satışta ve
  carilerde milyemli işlem, karşılığında altın veya döviz alma ve yalnız
  belge için girilen kayıtlar kullanılabilir.

- **Carilerde emanet, TC ve geçmiş tarih bakiyesi.** Emanet alındı ve
  teslim edildi hareketleri borç alacaktan ayrı izlenir. Cari kartına TC
  kimlik veya vergi numarası eklenebilir, ad yazarken kayıtlı müşteriler
  önerilir. Hareket satırına tıklandığında o tarihteki bakiye görünür; tüm
  carilerin ekstresi tek seferde Excel veya PDF olarak alınabilir.

- **İşlem fotoğrafları.** Sipariş, alacak, verecek ve cari kayıtlarına,
  ödeme hareketlerine ve barkodlu ürün kartlarına fotoğraf eklenebilir.
  Fotoğraflar müşterinin geçmiş ekranında işlem adıyla listelenir; konum
  bilgisi dahil ek veriler temizlenir.

- **Barkod serisi, kart ve stok uyumu, belge stoğu.** Barkod serisi
  işletme tarafından seçilebilir. Barkod kartlarının gramı ile stok
  arasında fark oluştuğunda ürünler ekranında uyum kutusu çıkar ve
  faturaların hangi kartlarla karşılandığı seçilebilir. Barkodla ürün
  takibi yapan işletmelerde fatura ve pusulalar vitrinden ayrı bir belge
  stoğunda izlenir. Etiket yazdırmadaki onay pencereleri bilgisayar başına
  bir kez yapılan ayarla kaldırılabilir.

- **e-Belge: kendi seri ile devam ve yer tutucu kimlik.** İzibiz portalında
  kendi belge serisini kullanan işletmelerde kesim portaldaki son
  numaradan devam eder; son belgeden eski tarihli işlem kesilmez ve sebebi
  gösterilir. Kimliği bilinmeyen bireysel alıcı için toplu kesim listesinde
  11111111111 yer tutucusu bilinçli olarak girildiğinde satır kesilir ve
  ayrı işaretle görünür.

### Düzeltildi

- Aynı gün aynı kişiden gelen parçalı ödemeler, ad farklı yazıldığında
  ayrı belgeye bölünebiliyordu; artık kimlik numarası veya benzer ad
  üzerinden tek belgede birleşiyor.
- Bir bankanın anlık bildirimi masraf dahil, ekstresi masrafsız geldiğinde
  aynı ödeme için ikinci gider pusulası oluşabiliyordu; iki kayıt
  eşleştirilerek listede yalnız biri gösteriliyor.
- Bir alış-satış işlemi birden fazla kez düzenlendiğinde stoktan gram
  tekrar düşebiliyordu; geri alma hesabı düzeltildi.
- Bazı banka ekstrelerinde birden fazla satıra yayılan hareketler
  okunmuyordu; bu hareketler artık eksiksiz alınıyor.
- Geriye tarihli kesilen bazı e-Arşiv faturaları panelde
  görüntülenemiyordu; görüntüleme düzeltildi.
- Muhasebe sayfası açıldıktan sonra basılan termal fişler A4 ölçeğine göre
  küçülerek çıkabiliyordu; fiş artık her durumda yazıcının kağıt
  genişliğinde basılıyor.
- Makbuzlarda işletme adresindeki Türkçe karakterler kod olarak
  görünebiliyordu; düzeltildi.
- Tutardan gram hesabı yapıldıktan sonra miktar veya milyem
  değiştirildiğinde tutar eski değerde kalabiliyordu; tutar artık yeniden
  hesaplanıyor.
- Cari özetinde fiyat ekranında bulunmayan emtialar toplama katılmıyordu;
  bu kalemler artık ham alış fiyatı veya milyem ile has fiyatı üzerinden
  değerleniyor.
- Fiyat ekranında tam ekran geçişlerinde arka planda bağlantı
  birikebiliyordu; ekran artık tek bağlantıyla çalışıyor.

### İyileştirildi

- **Panel kullanımı.** Seçilen renk teması panelin tamamına uygulanıyor.
  Alış-satış formunda açıklama metinleri bilgi simgesine taşındı, alanlar
  daha az yer kaplıyor. Carilerde emtia listesi kuyumcu sırasına göre
  gruplandı, uzun emtia adları okunur hale getirildi.

### Önemli

- Gelişmiş Defter, milyemli işlem ve karşılığında ödeme yalnız işletme
  sahibinin açtığı Gelişmiş Defter anahtarıyla devreye girer; anahtar
  kapalı işletmelerde ekranlar ve kayıtlar eskisi gibi çalışır.
- Barkod etiketi çıktıları bu sürümdeki değişikliklerden etkilenmedi;
  fiyat ekranında yalnız bağlantı düzeltmesi yapıldı. Mevcut fatura ve
  pusula kayıtları değiştirilmedi.

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

### v2026.09.29

**Added** — Sales form: discount line, option to hide the labour line on the
receipt, and posting the unpaid balance to the customer account. Advanced
Ledger (optional) tracking cash, gold by carat, pure gold, FX, bank and POS
items with end-of-day rates and profit summaries. Customer accounts: custody
movements, national ID / tax number, balance at any past date, bulk
statements (Excel/PDF). Photos on orders, receivables, payments and barcode
cards. Selectable barcode series, card-to-stock reconciliation and a separate
document stock for shops that track items by barcode. e-Documents: continue
from the shop's own İzibiz series; placeholder ID for unnamed buyers.

**Fixed** — Several document, stock and receipt calculation issues, and
connection build-up on the price screen during full-screen switches.

**Note** — Advanced Ledger features only activate when the shop owner turns
them on. Barcode label output is unchanged; existing invoice and voucher
records were not modified.

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
