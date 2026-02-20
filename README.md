# ResNet50 ile Glokom Tespiti

Bu proje, **retinal fundus (göz dibi) görüntüleri** üzerinden  
**derin öğrenme** kullanarak otomatik **glokom tespiti** yapılmasını amaçlamaktadır.

Çalışmada transfer öğrenme yaklaşımı kullanılarak **ResNet50** mimarisi
üzerinde ikili sınıflandırma gerçekleştirilmiştir.

---

## 🧠 Model Mimarisi

- **Mimari:** ResNet50 (ImageNet ön eğitimli)
- **Görev:** İkili sınıflandırma
  - Glokom
  - Normal
- **Framework:** PyTorch

---

## 📊 Veri Kümesi

- **Kaynak:** ACRIMA retinal fundus veri seti
- **Veri Bölünmesi:**
  - %80 Eğitim
  - %20 Test
- Eğitim ve test görüntülerinin listeleri **tekrar üretilebilirlik**
  sağlamak amacıyla ayrı dosyalar halinde kaydedilmiştir.

---

## 🏋️ Eğitim Stratejisi

Eğitim süreci çok aşamalı olarak yürütülmüştür:

1. Standart eğitim / test bölünmesi ile başlangıç eğitimi  
2. Bağımsız test kümesi üzerinde değerlendirme  
3. **Yanlış Negatif (False Negative)** örneklerin analizi  
4. **Zor Örnek Madenciliği (Hard Example Mining)**  
5. Yanlış negatif örnekler üzerinde mini ince ayar (fine-tuning)

Bu yaklaşımın amacı, tıbbi tanı açısından kritik olan
**yanlış negatif oranını azaltmaktır**.

---

## 📈 Nihai Sonuçlar (Test Kümesi)

| Metrik      | Değer |
|-------------|-------|
| Doğruluk (Accuracy) | %100 |
| Kesinlik (Precision) | %100 |
| Duyarlılık (Recall) | %100 |
| F1-Skoru | %100 |
| ROC-AUC | %100 |

> ⚠️ **Önemli Not:**  
> Bu sonuçlar **aynı kaynaktan gelen test verisi** üzerinde elde edilmiştir.  
> Gerçek dünya genellemesi için **harici veri setleriyle doğrulama**
> yapılması gerekmektedir.

---

## 📁 Proje Dosyaları

- `glaucoma_resnet50.pth`  
  → İlk eğitilmiş temel model  

- `glaucoma_resnet50_finetuned.pth`  
  → Zor örnekler ile ince ayar yapılmış nihai model  

- `train_files.txt` / `test_files.txt`  
  → Sabit veri bölünmeleri  

- `results.txt`  
  → Değerlendirme sonuçları  

- `experiment.json`  
  → Deney ayarları ve hiperparametreler  

---

## 📝 Notlar ve Sınırlamalar

- Çalışma **aynı dağılıma sahip veri** üzerinde değerlendirilmiştir
- Harici veri setleri bu aşamada kullanılmamıştır
- Sonuçlar **deneysel ve araştırma amaçlıdır**
- Klinik kullanım için ek doğrulama gereklidir

---

## 🔮 Gelecek Çalışmalar

- Harici veri setleri ile doğrulama
- Veri setleri arası genelleme analizi
- Açıklanabilir yapay zekâ yöntemleri (Grad-CAM vb.)
- Klinik karar destek sistemlerine entegrasyon
