# Project 2 Planı: El yazısı harf üreten GAN

Bu planı birlikte değiştirebiliriz. Biten adımı `[x]` ile işaretleyelim.

## Hoca ne istiyor?

EMNIST Letters veri seti ile el yazısı harf resmi üreten bir **GAN** yapacağız.

| En yüksek not | Ne yapmalıyız |
|---|---|
| 3.0 | **Basic GAN**: rastgele harf üretir |
| 4.0 | **Conditional GAN**: kullanıcı harfi seçer, model o harfi üretir |
| 5.0 | **One-shot generation**: model, eğitimde **olmayan** bir harfi **tek bir örnekten** üretir |

Hedefimiz: **5.0** (farklı karar verirsek burayı değiştirelim).

## Önemli tarihler

| Tarih | Ne var |
|---|---|
| 2 Aralık 2026 | Hoca ile görüşme (mail gönderildi) |
| 15 Aralık 2026 | 5.0 için zorunlu görüşmenin son günü |
| 31 Aralık 2026 | Gece yarısından önce teslim (deadline: 1 Ocak, 00:01) |

## Teslim kuralları

- Proje 2 kişilik. Teslimi **tek kişi** yapar ve **iki öğrenci numarasını** yazar.
- Notebook içinde fikrimizi ve geliştirme sürecini anlatan yazılar olmalı.
- **Trial and error** göstermeliyiz. Kötü sonuçları silmeyelim.

## Temel kavramlar

- **Generator:** rastgele **noise** alır, harf resmi çizer.
- **Discriminator:** resme bakar, **real** mi **fake** mi diye karar verir.
- **Training:** ikisi yarışır. Discriminator sahteleri yakalamayı, generator onu kandırmayı öğrenir.
- **Batch:** bir seferde kullanılan resim grubu (örneğin 128).
- **Epoch:** tüm verinin bir kez görülmesi.
- **Loss:** modelin hata değeri.

## Bilgisayarda çalıştırma

1. `gan.ipynb` dosyasını VS Code ile aç.
2. GPU'lu PyTorch kur: `pip install torch torchvision --index-url https://download.pytorch.org/whl/cu126`
3. Şunları da kur: `pip install matplotlib ipykernel`
4. PyTorch kurulu olan Python **kernel**'ini seç.
5. **Run All** de. Veri ilk seferde `data/` klasörüne iner (büyük olduğu için git'e eklenmiyor).

NVIDIA ekran kartı yoksa: `pip install torch torchvision`. Training çok daha yavaş olur.

## Notebook'u nasıl yazıyoruz?

- Basit kod ve basit isimler.
- Açıklamalar basit **İngilizce** (bu plan Türkçe, notebook İngilizce).
- Her hücrede tek küçük adım.

## Adımlar

### Adım 0: Kurulum
- [x] PyTorch kur ve GPU'yu kontrol et
- [x] EMNIST Letters verisini indir
- [x] `gan.ipynb` dosyasını oluştur

### Adım 1: Veriyi tanıma (27 Kasım'a kadar)
Amaç: veride ne olduğunu görmek ve ağa hazırlamak.
- [x] Veriyi yükle (124.800 resim, 28x28, 26 harf)
- [x] Her harften bir resim göster
- [x] Sorun bulundu: resimler yan ve aynalı. Satır ve sütunları değiştirerek (**transpose**) düzelttik
- [ ] **Run All** yap (bazı isimleri değiştirdik)
- [ ] Aynı harfin farklı yazılışlarını göster
- [ ] **Normalization**: piksel değerlerini -1 ile 1 arasına getir

### Adım 2: Basic GAN, not 3.0 (28 Kasım'a kadar)
Amaç: harfe benzeyen resimler üretmek. Hangi harfin çıkacağını henüz seçemiyoruz.
- [ ] Generator ve discriminator ne yapar, öğren
- [ ] Trial 1: **linear layer**'lı basit GAN
- [ ] **Training loop** yaz
- [ ] Training sırasında örnek resimleri göster
- [ ] Trial 2: **convolution layer**'lı GAN (**DCGAN**)
- [ ] İki denemeyi karşılaştır ve gördüklerimizi yaz

### Adım 3: Harf seçme, not 4.0 (30 Kasım'a kadar)
Amaç: "B" deyince B üretmek.
- [ ] Harfin **label** bilgisini generator ve discriminator'a ver (**conditional GAN**)
- [ ] Fonksiyon yaz: girdi bir harf, çıktı o harfin resimleri
- [ ] Training yap ve kontrol et: harfler doğru mu?

### Adım 4: Yeni harf için ilk plan, not 5.0 (1 Aralık'a kadar)
Amaç: görüşmeden önce fikrimizi hazırlamak. Model yeni harfi tanımadığı için ona label veremeyiz, **örnek resim** vereceğiz.
- [ ] Bazı harfleri training'den çıkar (öneri: X, Y, Z)
- [ ] Modeli planla: generator, label yerine **tek bir örnek resim** ve noise alır
- [ ] Discriminator şunu kontrol eder: resim real mi ve örnekle aynı harf mi?

### Görüşme: 2 Aralık
- [ ] 1-3. adımların sonuçlarını göster
- [ ] 4. adımın planını anlat
- [ ] Sor: training'den kaç harf çıkarmalıyız?
- [ ] Sor: sonuçların kalitesini nasıl ölçmeliyiz?
- [ ] Sor: generation sırasında girdi olarak örnek resim vermek uygun mu?
- [ ] Hocanın önerilerini "Notlar" bölümüne yaz

### Adım 5: One-shot modelini eğitme (3-15 Aralık)
- [ ] Modeli kur ve eğit
- [ ] Çıkardığımız harflerle test et
- [ ] İyileştirmeye çalış, her denemenin sonucunu sakla

### Adım 6: Sonuçları değerlendirme (16-22 Aralık)
- [ ] Küçük bir **classifier** eğit: üretilen harfler doğru mu diye bakacak (sadece test için)
- [ ] Modelleri bir tabloda karşılaştır
- [ ] İyi ve kötü örnekleri göster

### Adım 7: Bitirme ve teslim (23-29 Aralık)
- [ ] Notebook'taki açıklamaları tamamla
- [ ] **Conclusion** yaz
- [ ] Baştan **Run All** yap, hata olmadığını kontrol et
- [ ] İki öğrenci numarasını ekle
- [ ] Bir kişi projeyi göndersin

## Kim ne yapacak?

| Adım | Kişi |
|---|---|
| 1 ve 2 | |
| 3 | |
| 4 ve 5 | |
| 6 ve 7 | İkimiz |

## Notlar
