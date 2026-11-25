Mevcut çek/senet Table ve Text Spotting Silver GT değerlendirmesini görsel olarak debug edebilmem ve gerektiğinde manuel doğrulayabilmem için bir inceleme arayüzü hazırla.

- Her görevden başarılı, düşük skorlu ve belirsiz örnekleri kapsayan yaklaşık 10–15 örnek seç. Özellikle %88 belirsizlik bulunan senet spotting'e ağırlık ver.
- Her örnekte orijinal görseli, PaddleOCR bounding box'larını ve okunan metinleri göster. Qwen referansını ve PaddleOCR çıktısını yan yana sun.
- Eşleşen, farklı okunan, eksik ve fazladan tespit edilen metinleri renklerle işaretle. Mümkünse görsel üzerinde ilgili bölgelerle ilişkilendir.
- Her örneğin skorunu, belirsizlik durumunu ve bu kararın hangi eşik veya kurala göre verildiğini göster. Qwen çıktı kesilmesi, metin sıralaması, normalizasyon ve eşleştirme hatalarını ayrı kategorilerde incele.
- Table örneklerinde PaddleOCR ve Qwen'in tablo yapılarını/hücre içeriklerini de yan yana karşılaştır.
- Qwen'in koordinat üretmediği alanlarda referans konum uydurma. Eşleşmelerin kesin mi yoksa tahmini mi olduğunu belirt.

Yerel, tarayıcıda açılabilen bir HTML debug raporu oluştur. Örnekler arasında gezinebileyim, görselleri yakınlaştırabileyim ve her örneği "Paddle doğru", "Qwen doğru", "İkisi de hatalı", "Kararsız" şeklinde manuel etiketleyip kısa not ekleyebileyim. Verdiğim kararlar dışa aktarılabilsin ve sonradan değerlendirmede kullanılabilsin.

Öncelikle kayıtlı görselleri ve model çıktılarını kullan; OCR/VL inference'ını yeniden çalıştırma. Mevcut skorları veya evaluation kodlarını değiştirme. Amaç, belirsizliklerin gerçek nedenlerini görsel olarak inceleyip değerlendirme sisteminin doğruluğunu manuel kontrol edebilmek.
