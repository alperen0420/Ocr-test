Mevcut değerlendirmedeki eksik kalan iki işi tamamla:

1. Seal: ICDAR 2023 ReST veri setini temin et, uygun GT'li örneklerle Seal evaluation'ını çalıştır ve metin tanıma ile end-to-end spotting metriklerini hesapla. Veri erişiminde sorun olursa uygun GT'li alternatif benchmark araştır.
2. Formula: UniMER için eksik kalan resmî CDM/ExpRate@CDM metriğini uygula ve mevcut sonuçlarla birlikte raporla. Resmî implementasyon ve normalizasyon kurallarını koru.

Mevcut başarılı değerlendirmeleri ve düzeltilmiş metrikleri değiştirme. Silver GT sonuçlarını mevcut belirsizlik ve güvenilirlik uyarılarıyla koru. Gereksiz model çağrısı veya tüm pipeline'ı yeniden çalıştırma; mümkün olan yerlerde kayıtlı çıktıları kullan.

Sonuç dosyalarını güncelle, yeni metrikleri doğrula ve tamamlanamayan bir işlem olursa nedenini açıkça belirt.
