Evaluation sonuçlarını incelemeni ve özellikle metodolojik geçerliliği kontrol etmeni istiyorum. Mevcut skorları doğrudan kabul etmeden aşağıdaki noktaları araştır:

1. Silver GT: %80 karşılıklı token kapsaması kuralının yanlış güven oluşturma riskini incele. Belirsiz örneklerin skor dışı kalmasından doğan selection bias'ı değerlendir. Özellikle senet spotting'de yalnızca 12/100 örneğin skorlanması nedeniyle sonucun temsil gücünü sorgula. Gerçek GT olmadan doğruluk iddiasında bulunma.
2. FUNSD: Sayfa düzeyi Word F1'in gerçek end-to-end spotting metriği olmadığını dikkate al. Satır/kelime granülerliği ve %3 x offset sorununu araştır; metin konumu ile tanıma doğruluğunu mümkünse ayrı ve birlikte ölçebilecek uygun yöntem öner.
3. Formula: ExpRate 0.50, CER 0.55 ve BLEU-4 0.94 sonuçlarının tutarlılığını kontrol et. Tokenizasyon, normalizasyon ve hesaplama kodlarını incele. UniMER'in resmî CDM metriğinin neden raporlanmadığını belirle.
4. Chart: Recall yanında precision/F1 hesaplanabilirliğini incele. 12/50 parse hatasının skora nasıl yansıdığını doğrula.
5. Table: APTED 250 düğüm sınırının örnekleri atlayıp atlamadığını veya skorları değiştirip değiştirmediğini kontrol et.
6. Qwen: Gerçek GT benchmark'larındaki kalibrasyonun çek/senet silver referanslarının güvenilirliğini ne ölçüde desteklediğini değerlendir.
7. Seal: Bu görevin neden çalıştırılmadığını ve tamamlanması için gerekenleri belirle.

Mevcut sonuç dosyalarını ve değerlendirme kodlarını incele. Gerçekten doğrulanmış sonuçları, metodolojik sınırlamaları ve hatalı/yanıltıcı metrikleri net biçimde ayır.

Bu aşamada kod değiştirme veya testleri yeniden çalıştırma. Önce bulguları önem derecesine göre sınıflandır, hangi sorunların düzeltilmesinin zorunlu olduğunu ve en az değişiklikle nasıl düzeltilebileceğini açıkla.
