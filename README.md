Mevcut OCR sisteminin Seal, Formula, Chart, Table ve Text Spotting görevlerindeki doğruluğunu ve performansını değerlendirmek için kapsamlı ancak pratik bir evaluation yaklaşımı tasarla. Hedef, manuel anotasyon gerektirmeden yaklaşık 1–2 saat içerisinde güvenilir ve yorumlanabilir sonuçlar elde etmek.

1. Benchmark veri setleri

Aşağıdaki veri setlerini araştır; GT erişilebilirliğini, resmî evaluation protokollerini ve mevcut sistemle uyumluluklarını doğrula:

- Seal: "ICDAR 2023 ReST" (https://rrc.cvc.uab.es/?ch=20) — Mühür metni tespiti ve tanıma.
- Formula: "UniMER" (https://huggingface.co/datasets/wanderkid/UniMER_Dataset) — Matematiksel ifade ve LaTeX doğruluğu.
- Chart: "Financial Chart OCR" (https://huggingface.co/datasets/varadsrivastava/financial-chart-ocr) — Grafik metinleri ve sayısal veri çıkarımı.
- Table: "PubTabNet" (https://www.paddleocr.ai/v3.6.0/en/datasets/table_datasets.html) — Tablo yapısı ve hücre içerikleri.
- Text Spotting: "FUNSD" (https://github.com/crcresearch/FUNSD) — Metin bölgelerinin tespiti ve tanınması.

Bunlar başlangıç adayları. GT, görev uyumu veya değerlendirme protokolü açısından daha uygun alternatifler varsa değerlendir. Resmî benchmark metriklerini mümkün olduğunca koru.

2. Mevcut çek/senet verileri ve VL kullanımı

Mevcut çek/senet verileri yalnızca Table ve Text Spotting görevlerinde kullanılacak. Seal, Formula ve Chart değerlendirmelerine kesinlikle dahil edilmeyecek.

Table ve Text Spotting görevleri hem gerçek GT içeren benchmark'larla hem de mevcut çek/senet verileriyle ayrı ayrı değerlendirilecek.

Çek/senet verilerinin GT'si bulunmuyor ve manuel kontrol yapılmayacak. Qwen 8B VL modelini otomatik referans oluşturmak ve belirsiz OCR çıktılarını doğrulamak amacıyla kullanabiliriz.

Değerlendirilecek yaklaşım:

- Qwen'in görselden PaddleOCR'dan bağımsız referans üretmesi.
- Gerekirse farklı prompt veya bölgesel kırpımlarla ikinci okuma yapılması.
- Uyuşmazlıkların tespit edilip yalnızca gerekli örneklerin yeniden doğrulanması.
- Çözülemeyen örneklerin belirsiz olarak işaretlenmesi.
- Qwen'in güvenilirliğinin, gerçek GT bulunan uygun benchmark örneklerinde ayrıca test edilmesi.

VL çıktısını kesin GT kabul etme. Gerçek GT ile silver/pseudo-GT sonuçlarını ayrı raporla. Qwen'in kendi hatalarının OCR performansını yanıltmasını mümkün olduğunca engelle.

Belgelerin gerçek yapısına uygun metrikler seç; güvenilir koordinat GT'si olmadan kesin detection skoru hesaplama.

3. Örnek sayısı ve metrikler

Başlangıç için her benchmark'tan 50, çek ve senetlerden 100'er örnek olmak üzere toplam 450 görsel düşünülebilir. Bu dağılım zorunlu değil; doğruluk, temsil gücü ve çalışma süresine göre optimize et.

Farklı zorluk seviyeleri, belge türleri ve görüntü kaliteleri temsil edilmeli. Tekrarlı/çok benzer örneklerden kaçınılmalı.

Değerlendirme için aday metrikler:

Görev| Metrikler
Seal| End-to-end spotting F1, CER
Formula| ExpRate, CDM, CER
Chart| Sayısal veri doğruluğu, metin doğruluğu
Table| TEDS, hücre/yapı doğruluğu
Text Spotting| Detection F1, IoU, CER
Çek/Senet (yalnızca Table ve Spotting)| VL referansına göre CER, coverage, alan eşleşmesi ve uygulanabilir yapısal metrikler

Metrikleri benchmark protokollerine göre kesinleştir. Format farklılıklarının yapay hatalara neden olmaması için uygun normalizasyon ve eşleştirme yöntemleri belirle. Mümkünse güven aralıkları ve hata türlerini de raporla.

4. Sistem uyumluluğu ve süre

Mevcut PaddleOCR sürümünü, kullanılan pipeline'ları ve çıktı formatlarını incele. Hangi görevlerin doğrudan desteklendiğini, hangilerinin ek bileşen gerektirdiğini belirle. Desteklenmeyen bir çıktıyı yanlış biçimde OCR başarısızlığı olarak değerlendirme.

VL tarafındaki mevcut ölçüm yaklaşık 8 paralel istek / 15 saniye. OCR çok daha hızlı; darboğaz VL inference.

Bu nedenle gereksiz VL çağrılarını azaltan, paralelliği kullanan ve yalnızca belirsiz örnekleri tekrar değerlendiren bir akış tasarla. Tahmini istek sayısını ve toplam süreyi hesapla. Doğruluğun yanında latency, p50/p95, throughput ve başarısız işlem oranlarını da ölç.

5. Beklenen sonuç

Önce yalnızca araştırma ve tasarım yap, kodlama veya evaluation çalıştırma.

Nihai planda şunlar net olsun:

1. Kullanılacak veri setleri, GT durumları ve evaluation protokolleri.
2. Görev bazında örnek sayıları ve seçim stratejisi.
3. PaddleOCR bileşenleri ve kesin metrikler.
4. Qwen ile otomatik GT üretimi, doğrulama ve belirsizlik yönetimi.
5. Uçtan uca evaluation akışı, paralellik ve tahmini süre.
6. Sonuç raporlama biçimi, güvenilirlik sınırları ve olası hata kaynakları.

Amaç gereksiz karmaşıklık yaratmadan kısa sürede, tekrarlanabilir, teknik olarak savunulabilir ve gerçek performansı mümkün olduğunca doğru yansıtan bir değerlendirme sistemi kurmak. Kararları mevcut altyapıya göre ver ve önemli tercihlerini gerekçelendir.
