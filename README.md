Cleaned vs Dirty Sınıflandırma Projesi
📄 Proje Açıklaması
Bu proje, Kaggle "Cleaned vs Dirty" veri seti kullanılarak temiz (cleaned) ve kirli (dirty) görsellerin sınıflandırılmasını hedeflemektedir. Temel bir Convolutional Neural Network (CNN) modeliyle, görsellerin sınıf etiketlerine göre ayrılması sağlanmıştır. Projede, veri artırma teknikleri ve sınıf dengesizliğine yönelik optimizasyonlar uygulanarak doğruluğu yüksek bir model geliştirilmiştir.

📁 Veri Seti
Projede kullanılan veri seti şu bileşenlerden oluşmaktadır:

Eğitim Verileri (Train Data): data/train/ dizininde bulunan, modelin öğrenmesi için kullanılan görseller.
Test Verileri (Test Data): data/test/ dizininde bulunan, modelin başarımını ölçmek için kullanılan görseller.
Etiketler (Labels): Görsellerin temiz ya da kirli olduğunu belirten sınıf etiketleri, data/sample_submission.csv dosyasında yer alır.
Veri Seti Özellikleri:
Görseller çeşitli açılardan çekilmiş temiz ve kirli tabak görsellerini içermektedir.
Sınıf dengesizliği gözlemlenmiş ve bu durum veri artırma yöntemleriyle ele alınmıştır.
🛠️ Proje Adımları
1. Veri Ön İşleme
Veri ön işleme aşamasında şu adımlar gerçekleştirilmiştir:

Boyutlandırma: Görseller, CNN modeline uygun olacak şekilde 224x224 piksel boyutuna küçültülmüştür.
Normalizasyon: Görsel pikselleri, 0 ile 1 arasında ölçeklendirilmiştir.
Veri Artırımı (Augmentation):
Döndürme (Rotation): Görseller rastgele belirli açılarla döndürülmüştür.
Yatay Çevirme (Horizontal Flip): Görseller, ayna görüntüsü olarak çevrilmiştir.
Renk Yoğunluğu Değiştirme: Görsellerdeki parlaklık ve kontrast değerleri değiştirilmiştir.
2. Model Geliştirme
Proje kapsamında aşağıdaki CNN modeli geliştirilmiştir:

Katmanlar:
İki adet evrişim (convolution) ve maksimum havuzlama (max pooling) katmanı.
Dropout ve aktivasyon fonksiyonlarıyla (ReLU) desteklenmiş bir fully connected katman.
Eğitim Ayrıntıları:
Optimizer: Adam
Kayıp Fonksiyonu: Categorical Cross-Entropy
Epoch: 20
3. Model Eğitimi
Model eğitimi sırasında:

Eğitim ve doğrulama verileri, %80-%20 oranında ayrılmıştır.
Class Weights yöntemiyle sınıf dengesizliği optimize edilmiştir.
Modelin doğruluk ve kayıp değerleri her epoch sonunda kaydedilmiştir.
4. Model Değerlendirmesi
Model performansı şu metriklerle analiz edilmiştir:

Accuracy (Doğruluk): Modelin genel doğruluk oranı hesaplanmıştır.
Confusion Matrix: Temiz ve kirli sınıflar için doğru/yanlış tahminler görselleştirilmiştir.
Sınıflandırma Raporu: Doğruluk, kesinlik (precision), hatırlama (recall) ve F1 skoru gibi detaylı metrikler raporlanmıştır.
🏆 Sonuçlar
Genel Doğruluk: %97.3
Confusion Matrix:
Modelin tahmin sonuçları aşağıdaki tabloda verilmiştir:
Gerçek (Actual) \ Tahmin (Predicted)	Cleaned	Dirty
Cleaned	18	2
Dirty	18	706
Model, test verisi üzerinde sınıflandırma başarısını etkili bir şekilde kanıtlamıştır.
🚀 Nasıl Çalıştırılır?
Gereksinimler
Projenin çalışması için gerekli bağımlılıkları yükleyin:

bash
Kodu kopyala
pip install -r requirements.txt
Adımlar
Veri Ön İşleme: src/data_preprocessing.ipynb dosyasını çalıştırarak veri yükleme ve ön işleme işlemlerini gerçekleştirin.
Model Eğitimi: src/model_training.ipynb dosyasını çalıştırarak modeli eğitin.
Sonuç Analizi: Eğitim sonuçlarını ve görselleri results/ dizininden inceleyin.
📂 Dosya Yapısı
src/data_preprocessing.ipynb: Veri yükleme ve ön işleme adımları.
src/model_training.ipynb: Modelin eğitilmesi ve değerlendirilmesi.
requirements.txt: Kullanılan Python kütüphanelerinin listesi.
results/: Model performans görselleri ve çıktı sonuçları.
🔗 Veri Seti
Veri setine Cleaned vs Dirty Dataset bağlantısından ulaşabilirsiniz. Veri seti, aşağıdaki dizinlere yerleştirilmelidir:

data/train/: Eğitim verileri.
data/test/: Test verileri.
data/sample_submission.csv: Sınıf etiketleri dosyası.
