
# 📶 Yapay Zeka ile İnternet Kullanım Derecesinin Ölçülmesi ve Tahmini

Bu proje, gençler ve çocuklar arasında artan **problemli internet kullanımını** tespit etmek ve tahmin etmek amacıyla yapay zeka temelli bir sistem geliştirmektedir. Kaggle platformundaki **Healthy Brain Network** veri seti kullanılarak makine öğrenmesi, zaman serisi analizi, LSTM ve Prophet gibi teknikler kullanılmıştır.

📁 **Proje Sahipleri**:
- Ali Can Ayhan    
- Edanur Yıldız  
- Gülsüm Küntür  

🎓 **Danışman**: Doç. Dr. Murtaza Cicioğlu  
🏫 **Üniversite**: Bursa Uludağ Üniversitesi – Bilgisayar Mühendisliği  
📅 **Yıl**: 2024-2025  

---

## 📦 Kullanılan Veri Seti

- **Adı**: Healthy Brain Network (HBN)  
- **Kaynak**: [Kaggle](https://www.kaggle.com/competitions)
- **İçerik**: 5-22 yaş aralığında bireylere ait fiziksel ölçümler, anket verileri, ve 996 kişiye ait akıllı saat zaman serisi verileri.  
- **Formatlar**: `train.csv`, `series_train.parquet`, `test.csv`, `series_test.parquet`  
- Veri seti ciddi oranda eksik veri içermektedir, bu yüzden eksik veri işleme ve veri artırma yöntemleri kullanılmıştır.

---

## 🔍 Kullanılan Yöntemler

### 🔹 Veri İşleme
- Eksik veriler için: GroupBy + ortalama, Bayesian Ridge, KNN Imputer
- Korelasyon analizi ve gürültü azaltma
- SMOTENC ile dengesiz veri sınıflarının dengelenmesi

### 🔹 Özellik Mühendisliği
- Zaman serisi üzerinden:  
  - Ortalama uyku süresi çıkarımı  
  - 1 dakikalık pencere bölme  
  - Prophet ve LSTM ile yeni değişken üretimi  

### 🔹 Modelleme
- LightGBM, XGBoost, HistGBM
- CatBoost Regressor
- Ensemble (çoğunluk oylaması)  
- Sınıflandırma problemi regresyon problemlerine dönüştürülerek çözülmüştür  

### 🔹 Performans Ölçümü
- **Metric**: Quadratic Weighted Kappa (QWK)  
- **En iyi private score**: 0.486

---

## 📁 Proje Klasörleri (Önerilen Yapı)

```
📂 data/                   # Veri seti (train.csv, test.csv, series_*.parquet)
📂 notebooks/              # Jupyter / Kaggle Notebook dosyaları
📂 models/                 # Kaydedilen modeller ve sonuç analizleri
📂 utils/                  # Yardımcı Python dosyaları (veri işleme, görselleştirme)
📄 README.md               # Bu dosya
```

---

## 📊 Sonuçlar ve Kazanımlar

| Yöntem | QWK (Private) |
|--------|---------------|
| LSTM tabanlı ensemble model | 0.422 |
| Prophet tabanlı ensemble model | 0.420 |
| PCIAT formülü + ensemble | 0.433 |
| SMOTENC + model | 0.358 |
| Ham veri ile model | 0.298 |

> 🏆 **Sonuç**: LSTM ve PCIAT destekli ensemble modeller en başarılı sonuçları vermiştir.

---

## 🙏 Teşekkür

Bu projenin gerçekleştirilmesinde bizlere rehberlik eden, kıymetli katkıları ve desteğiyle yolumuzu aydınlatan **Doç. Dr. Murtaza Cicioğlu** hocamıza sonsuz teşekkürlerimizi sunarız.

---

## 📌 Not

Bu çalışma Bursa Uludağ Üniversitesi Bilgisayar Mühendisliği Bölümü 2024-2025 yılı tasarım projesi kapsamında gerçekleştirilmiştir. Akademik amaçla sunulmuştur.
