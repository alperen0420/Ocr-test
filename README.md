Mevcut OCR evaluation sisteminin son doğruluk ve tutarlılık denetimini (evaluation audit) gerçekleştir.

1. Skorlama kontrolü: CER, NED, CDM/ExpRate, TEDS, Chart metrikleri ve Spotting F1 hesaplamalarını incele. GT–tahmin eşleştirmelerini, normalizasyonları, koordinat dönüşümlerini, örnek dışlama kurallarını ve hata durumlarını doğrula.

2. Örnek bazlı doğrulama: Her görevden rastgele ve farklı hata türlerini temsil eden 5–10 örnek seç. Kayıtlı GT, model çıktısı ve hesaplanan skorları bağımsız olarak yeniden karşılaştır. Özellikle daha önce düzeltme yapılan metriklere ve şüpheli sonuçlara odaklan.

3. Silver GT kontrolü: Qwen referanslarının tutarlılığını, belirsizlik eşiklerini ve skorlanan/skorlanmayan örneklerin dağılımını incele. Selection bias ve olası yanıltıcı başarı oranlarını tespit et. Gerçek GT olmayan sonuçları kesin doğruluk olarak yorumlama.

4. Tekrarlanabilirlik: Mevcut kayıtlı çıktılardan skorları yeniden hesaplayarak raporlanan sonuçlarla karşılaştır. Örnek sayılarının, başarısız işlemlerin ve değerlendirme kapsamının tutarlı olduğunu doğrula.

5. Nihai rapor: Doğrulanan metrikleri, tespit edilen sorunları, yapılan zorunlu düzeltmeleri ve kalan metodolojik sınırlamaları açıkça belirt. Gerçek GT ve Silver GT sonuçlarını ayrı sun.

Tüm OCR/VL inference sürecini yeniden çalıştırma, gereksiz model çağrısı yapma. Öncelikle mevcut çıktıları kullan. Yalnızca doğrulanmış hesaplama hatalarını ve bunlardan etkilenen sonuçları düzelt; çalışan diğer bölümlere dokunma.

Amaç yeni bir değerlendirme tasarlamak değil, mevcut sonuçların doğru hesaplandığını, tutarlı ve tekrarlanabilir olduğunu son kez doğrulamak ve çalışmayı tamamlamak.
