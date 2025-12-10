# Standardized Test Question Difficulty Prediction
Bu proje, standart test sorularının (SAT, ACT, GRE, GMAT vb.) zorluk seviyesini Easy / Moderate / Hard olarak tahmin etmek amacıyla geliştirilmiştir.
Makine öğrenimi modelleri kullanılarak önce sayısal regresyon, ardından sınıflandırma tabanlı yaklaşımlar denenmiş ve en başarılı model belirlenmiştir.

## Projenin Amacı
Geleneksel olarak soru zorluk seviyeleri uzmanlar tarafından manuel olarak belirlenir. Bu süreç zaman alıcıdır ve her soruda tutarlı değerlendirme yapmak zordur. Bu proje şu sorulara yanıt aramaktadır:
Soru metninin uzunluğu

- Test türü

- Konu alanı

- Okunabilirlik seviyesi

- Seçenek sayısı

- Hesap makinesi gerektirip gerektirmemesi
Bu özelliklerin zorluk seviyesi üzerindeki etkisi analiz edilmiştir.

## Dataset Hakkında
Dataset, standart test sorularına ait 100 örnekten oluşmaktadır. Her soru şu bilgileri içerir:

- Test_Name (SAT Math, GRE Verbal, ACT, GMAT…)

- Topic_Area (Algebra, Reading, Data Insights…)

- Question_Text

- Options_Count

- Question_Length_Words

- Readability_Grade

- Requires_Calculator

- Difficulty_Level (Easy, Moderate, Hard → hedef değişken)
Hedef değişken:

Easy = 0

Moderate = 1

Hard = 2

Dataset temizdir ve eksik değer bulunmamaktadır.

## Keşifsel Veri Analizi
Notebook içinde aşağıdaki analizler yapılmıştır:

#### Difficulty Level dağılımı

→ Dataset dengesiz, Moderate sınıfı çok az.

#### Topic Area frekans grafiği

→ “Math” ve “Reading” kategorileri baskın.

#### Question Length histogramı

→ Uzun metinler genelde daha yüksek zorlukla ilişkili.

#### Readability Grade histogramı

→ Orta seviyede yoğunlaşmış.
Bu analizler, model seçiminde önemli bir temel oluşturmuştur.
## Kullanılan Modeller

Bu projede üç farklı model denenmiştir:

#### Linear Regression

- Regression modeli sınıflandırma problemine uygun değildir.

- Sayısal tahmin üretir, sınıfı direkt veremez.

- R² negatif → Yetersiz performans.

####  Logistic Regression

- Çok sınıflı sınıflandırma için uygundur.

- Hard sınıfında güçlü performans (%82 recall).

- Moderate sınıfında başarısız → Veri az.

####  Random Forest Classifier (Final Model)

- Küçük ve dengesiz veri setlerinde kararlı.

- Easy ve Hard sınıflarında en iyi performans.

- Doğrusal olmayan ilişkileri öğrenebilir.

- Bu nedenle final model olarak seçilmiştir.
