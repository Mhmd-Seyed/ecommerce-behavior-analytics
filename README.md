# ecommerce-behavior-analytics
E-Commerce Customer Behavior Analytics using PySpark.

# E-Ticaret Müşteri Davranışı Analitiği (PySpark)

Bu proje, büyük ölçekli e-ticaret tıklama akışı (clickstream) verilerini **Apache Spark (PySpark)** kullanarak işlemek ve satışa dönüşüm oranlarını artıracak müşteri davranış örüntülerini ortaya çıkarmak amacıyla geliştirilmiştir.

## Proje Tanımı
* **Problem:** Milyonlarca görüntüleme (`view`), sepete ekleme (`cart`) ve satın alma (`purchase`) olayından anlamlı müşteri davranışlarının çıkarılması.
* **Araştırma Sorusu:** Büyük clickstream verisinden satışa dönüşümü artıracak hangi bilgiler çıkarılabilir?

---

## Kullanılan Teknolojiler ve Veri Seti
* **Büyük Veri İşleme:** Apache Spark (`PySpark`), Spark SQL
* **Makine Öğrenmesi:** Spark MLlib (`LogisticRegression`, `RandomForest`, `KMeans`)
* **Görselleştirme:** Pandas, Matplotlib, Seaborn, Plotly
* **Geliştirme Ortamı:** Google Colab & GitHub
* **Veri Seti:** REES46 eCommerce Behavior Data (Kaggle)

---

## Ekip Görev Dağılımı ve Notebook Yapısı

| Görev | Sorumluluk Alanı | Çalışma Dosyası |
| :--- | :--- | :--- |
| **Öğrenci 1** | Clickstream veri setini hazırlar, temizler ve olay türlerini modeller (`Parquet` çıktısı üretir). | `notebooks/01_data_prep.ipynb` |
| **Öğrenci 2** | Kullanıcı oturumlarını (`user_session`) oluşturur; `görüntüleme → sepet → satın alma` dönüşüm oranlarını hesaplar. | `notebooks/02_sessions_conversion.ipynb` |
| **Öğrenci 3** | Spark ile ürün, kategori, saat ve müşteri segmenti bazında çok boyutlu analizler yapar. | `notebooks/03_spark_multidimensional_analysis.ipynb` |
| **Öğrenci 4** | Satın alma olasılığı tahmini veya RFM tabanlı müşteri segmentasyonu modeli geliştirir. | `notebooks/04_ml_purchase_segmentation.ipynb` |
| **Öğrenci 5** | Funnel (huni) analizi, veri görselleştirme ve farklı veri boyutlarında Spark performans karşılaştırması yapar. | `notebooks/05_funnel_and_benchmark.ipynb` |

---

## Ortak Veri Şeması (Data Schema Contract)

Tüm ekip üyelerinin kodlarının uyum içinde çalışması için `events_clean.parquet` dosyasında standartlaştırılan sütun yapısı:

* `event_time` (`Timestamp`): Olayın gerçekleştiği zaman damgası
* `event_type` (`String`): Etkileşim türü (`view`, `cart`, `purchase`)
* `product_id` (`Integer`): Ürün kimlik numarası
* `category_code` (`String`): Ürün ana ve alt kategorisi (örn. `electronics.smartphone`)
* `brand` (`String`): Marka adı
* `price` (`Float`): Ürün fiyatı
* `user_id` (`Integer`): Kullanıcı kimlik numarası
* `user_session` (`String`): Kullanıcı oturum kimliği (UUID)

---

## Çalışma ve Senkronizasyon Kuralları
1. **Veri Paylaşımı:** Büyük boyutlu `.csv` ve `.parquet` dosyaları GitHub'a yüklenmez; ortak Google Drive klasörü (`ecommerce_project`) üzerinden paylaşılır.
2. **Kod Güncelleme:** Her öğrenci yalnızca kendi numarasına ait `.ipynb` dosyasında çalışır ve değişikliklerini Colab üzerinden **File → Save a copy in GitHub** adımıyla kaydeder.
