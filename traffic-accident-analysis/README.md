# 🚗 UK Traffic Accidents Analysis (2000–2016)

Bu proje, 2000–2016 yılları arasında Birleşik Krallık'ta gerçekleşmiş **1.6 milyondan fazla trafik kazası** verisini analiz etmeyi amaçlamaktadır. Kazaların sebeplerini, zamansal desenlerini ve bölgesel farklılıkları anlamak için kapsamlı bir veri analizi ve modelleme süreci gerçekleştirilmiştir.

## 📁 Veri Seti

- **Kaynak:** [Kaggle - UK Traffic Flow](https://www.kaggle.com/daveianhickey/2000-16-traffic-flow-england-scotland-wales)
- **İçerik:** 1.6 milyon trafik kazası verisi
- **Kapsam:** 2000 - 2016 yılları arasında İngiltere, Galler ve İskoçya
- **Özellikler:**
  - Kaza şiddeti (Slight, Serious, Fatal)
  - Gün, saat, hava durumu, yol durumu
  - Kırsal/kentsel ayrımı
  - Polis müdahalesi bilgisi
  - GPS koordinatları

---

## 🎯 Amaç ve Anahtar Sorular

- 🛣️ **Trafik akışındaki değişim kazaları nasıl etkiler?**
- 🧪 **Kaza oranlarını artıran faktörler nelerdir?**
- 📈 **Zaman serisi tahmini ile gelecek kazalar öngörülebilir mi?**
- 🏙️ **Kırsal ve kentsel alanlar kazalarda nasıl farklılaşıyor?**

---

## 🔍 Veriye İlk Bakış

- Eksik değer analizi yapılmış ve uygun tekniklerle işlenmiştir.
- Tarih ve saat kolonları datetime formatına çevrilmiştir.
- Şehir içi ve kırsal bölgeler, yol sınıfı, hava koşulları gibi nitelikler kategorik olarak düzenlenmiştir.

---

## 📊 Veri Analizi & Görselleştirme

### Genel Bulgular:

- ☀️ **Kaza sayıları yaz aylarında artmakta** ve hafta içi günlerde daha yoğundur.
- 🌧️ **Hava ve yol durumu**, kazaların şiddeti üzerinde önemli bir etkiye sahiptir.
- 🌆 **Kırsal alanlardaki kazalar**, şehir içindekilere göre **daha ölümcül** sonuçlanmaktadır.
- 🚔 Polis müdahalesinin olup olmaması, kazanın ciddiyetiyle ilişkili olabilir.

### Görselleştirilen Konular:
- Kaza şiddeti dağılımı (pie chart)
- Günlük ve saatlik kaza yoğunluğu (bar & hist)
- Hava ve yol durumu ile kaza ilişkisi (countplot)
- Kırsal vs Kentsel alan karşılaştırması (pie chart)
- Yıllara ve aylara göre trend analizi (line plot)
- Kazazede sayısı dağılımı

---

## ⏳ Zaman Serisi Tahmini – Prophet Modeli

- Facebook’un Prophet kütüphanesi kullanılarak yıllık kaza sayılarının trendi tahmin edilmiştir.
- Model doğruluğu tatmin edici düzeydedir.
- Gelecek yıllar için kaza sayısı projeksiyonu yapılmıştır.

> **Sonuç:** Prophet modeli ile zaman serisi tahmini başarıyla gerçekleştirilmiştir.

---

## 📂 Kullanılan Kütüphaneler

```python
pandas, numpy, matplotlib, seaborn, plotly, prophet, scikit-learn
