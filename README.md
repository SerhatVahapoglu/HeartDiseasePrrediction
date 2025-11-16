*❤️ Heart Disease Prediction with ML & ANN

Bu proje, kalp hastalığı riskinin tahmini için klasik makine öğrenmesi modelleri ve yapay sinir ağı (MLP — Multi-Layer Perceptron) kullanan bir sınıflandırma çalışmasıdır.

Kullanılan veri seti: Heart Disease Dataset
Hedef değişken: target (0 = yok, 1 = var)

📌 Proje Amaçları

Veri temizleme ve ön işleme

One-Hot Encoding

Sayısal değişkenlerin standartlaştırılması

ML modelleri ile karşılaştırma

MLP modeli için optimizer / dropout / LR tuning

AUC-ROC ve Accuracy değerlendirmesi

Sonuçları tablo halinde yorumlama

📂 Kullanılan Modeller

Projede aşağıdaki algoritmalar kullanıldı:

Model	Accuracy	AUC
Logistic Regression	0.8524	0.9058
Random Forest	0.8032	0.8912
MLP (Adam)	0.8524	0.9118
MLP (Nadam)	0.8197	0.9069
MLP (RMSprop)	0.8524	0.9037
🧠 Model Performanslarının Yorumlanması
1) En yüksek AUC:

MLP (Adam) → AUC = 0.9118

AUC, modelin sınıflar arasındaki ayrımı ne kadar iyi yaptığını gösterir.
0.90 üzeri AUC, çok güçlü bir sınıflandırıcı demektir.

2) En yüksek accuracy

Logistic Regression ve MLP (Adam) aynı accuracy’ye sahip: 0.8524

Ancak MLP’nin AUC değeri daha yüksek olduğu için MLP (Adam) daha iyi bir genel model.

3) Random Forest

Beklenenin aksine bu dataset için LR ve MLP kadar iyi performans göstermedi.
Neden?

Veri küçük

Ağaç temelli modeller küçük ve çok dengesiz feature setlerinde bazen overfit olur

Lojistik Regresyon daha stabil çalışır

🔧 Yapılan Tuning’ler

MLP modeli üzerinde aşağıdakiler denendi:

✔️ Optimizer tuning

Adam (📈 en iyi sonuç)

Nadam

RMSprop

✔️ Learning Rate tuning

0.0001 – 0.001 – 0.005 — 0.01 aralıklarında test edildi.

✔️ Dropout tuning

%10 – %20 – %30 dropout hızları denendi.

✔️ Batch size tuning

16 – 32 – 64 batch boyutları test edildi.

Çeşitli tuning denemelerine rağmen Adam optimizer + Dropout(0.2) + LR = 0.001 en iyi kombinasyon olarak kaldı.

🧪 Veri Ön-İşleme

Projede aşağıdaki işlemler yapılmıştır:

Eksik veya hatalı kategori değerlerinin mode ile düzeltilmesi

cp, restecg, slope, ca, thal için One-Hot Encoding

age, chol, thalach, oldpeak gibi sayısal kolonların StandardScaler ile ölçeklenmesi

Outlier analizi (boxplot)

Veri setinin %80 train – %20 test şeklinde ayrılması

🧵 Kullanılan ANN Mimarisinin Özeti
Dense(32, relu)
Dropout(0.2)
Dense(16, relu)
Dropout(0.2)
Dense(1, sigmoid)


Loss → binary_crossentropy
Metrics → accuracy, AUC

📊 Neden AUC Kullanıyoruz?

Accuracy tek başına yeterli değil çünkü:

Veri dengesiz olabilir

Accuracy yüksek olsa bile pozitif sınıfları kaçırabilir

AUC–ROC, modelin sınıfları ayırma becerisini gösterir.
Bu projede sonuçlar 0.90+ AUC seviyesindedir ve bu oldukça güçlü performanstır.

🔥 Sonuç & Değerlendirme

Bu proje sonucunda:

Logistic Regression ve MLP modelleri başarılı ve stabil sonuçlar verdi.

En güçlü model MLP (Adam optimizer) oldu.

Random Forest bu veri setinde beklenen performansı göstermedi.

ANN tuning çalışmaları, AUC değerini anlamlı şekilde yükseltti.

Genel olarak proje, kalp hastalığı tahmininde derin öğrenmenin klasik makine öğrenmesine göre daha iyi ayrıştırma gücü sunduğunu gösterdi.**
