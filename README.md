# 🛰️ Uydu Görüntülerinden GES Tespiti

Bu proje, uydu görüntülerinden **Güneş Enerji Santrali (GES) bölgelerinin otomatik olarak tespit edilmesi** amacıyla geliştirilmiştir.

Çalışmada piksel seviyesinde segmentasyon yaklaşımı kullanılarak uydu görüntülerindeki GES alanlarının belirlenmesi hedeflenmiştir.

## 🎯 Projenin Amacı

Güneş enerji santrallerinin uydu görüntülerinden otomatik olarak tespit edilmesi; geniş bölgelerin incelenmesi, enerji altyapısının izlenmesi ve arazi kullanım analizleri gibi alanlarda kullanılabilecek bir görüntü işleme uygulamasıdır.

Bu projede derin öğrenme tabanlı bir **semantic segmentation** yaklaşımı kullanılarak GES bölgelerinin görüntü içerisindeki konumları piksel seviyesinde belirlenmiştir.

## 🧠 Kullanılan Model

Projede **Attention U-Net** mimarisi ve **ResNet34 encoder** kullanılmıştır.

Modelin genel yapısı:

```text
Uydu Görüntüsü
      ↓
ResNet34 Encoder
      ↓
Attention U-Net
      ↓
GES Segmentasyon Maskesi
      ↓
Dense CRF
      ↓
İyileştirilmiş GES Maskesi
```

### ResNet34

ResNet34, uydu görüntülerinden farklı seviyelerde görsel özelliklerin çıkarılması amacıyla encoder olarak kullanılmıştır.

### Attention U-Net

Attention mekanizması sayesinde modelin görüntü içerisindeki GES bölgelerine daha fazla odaklanması amaçlanmıştır.

### Dense CRF

Model tarafından oluşturulan segmentasyon sonuçları **Conditional Random Field (CRF)** kullanılarak iyileştirilmiştir. Böylece tahmin edilen bölgelerin sınırlarının daha doğru hale getirilmesi hedeflenmiştir.

## 📊 Veri Seti

Projede **"PV segmentation from satellite and aerial imagery"** veri setinden yararlanılmıştır.

Veri setinde:

* Uydu görüntüleri
* GES bölgelerini gösteren maske görüntüleri
* Piksel seviyesinde etiketlenmiş GES alanları

bulunmaktadır.

Bu çalışmada **138 eşleşmiş görüntü-maske örneği** kullanılmıştır.

Veri seti:

* **%80 Eğitim:** 110 görüntü
* **%20 Doğrulama:** 28 görüntü

olacak şekilde ayrılmıştır.

> Veri setinin tamamı telif/boyut ve kullanım koşulları nedeniyle bu repository içerisinde paylaşılmamıştır.

## 🔧 Veri Ön İşleme

Görüntülerin modele hazırlanması sırasında çeşitli ön işleme ve veri artırma (augmentation) tekniklerinden yararlanılmıştır.

Uygulanan işlemler arasında:

* Görüntülerin RGB formatına dönüştürülmesi
* Maskelerin grayscale olarak okunması
* Maskelerin binary formata dönüştürülmesi
* Görüntülerin yeniden boyutlandırılması
* Normalizasyon
* Random rotation
* Horizontal / vertical flip
* Ölçekleme ve kaydırma
* Parlaklık ve kontrast değişiklikleri
* Bulanıklık gibi augmentation işlemleri

yer almaktadır.

## ⚙️ Kullanılan Teknolojiler

* Python
* PyTorch
* Segmentation Models PyTorch
* Albumentations
* OpenCV
* NumPy
* Matplotlib
* scikit-learn
* Dense CRF
* Google Colab
* CUDA / GPU

## 📈 Model Değerlendirmesi

Modelin GES segmentasyon performansı aşağıdaki metrikler kullanılarak değerlendirilmiştir:

* **IoU (Intersection over Union)**
* **Dice Score**

Bu metrikler, model tarafından oluşturulan segmentasyon maskelerinin gerçek maskelerle ne kadar örtüştüğünü değerlendirmek için kullanılmıştır.

## 🖥️ Çalışma Ortamı

Proje **Google Colab** üzerinde GPU kullanılarak geliştirilmiş ve test edilmiştir.

Notebook içerisinde GPU kullanımı ve CUDA tabanlı PyTorch kurulumu için gerekli adımlar bulunmaktadır.

## 📁 Proje İçeriği

```text
uydu-goruntulerinden-ges-tespiti/
│
├── README.md
│
└── uydu_goruntulerinden_ges_tespiti.ipynb
```

Notebook içerisinde;

* Veri setinin hazırlanması
* Görüntü-maske eşleştirme
* Train/validation ayrımı
* Veri artırma
* Model oluşturma
* Model eğitimi
* Validation
* Dense CRF ile tahminlerin iyileştirilmesi
* Test ve görselleştirme

adımları bulunmaktadır.

## 💡 Projede Kazanılan Deneyimler

Bu proje kapsamında;

* Semantic segmentation
* Attention U-Net
* ResNet tabanlı encoder kullanımı
* Uydu görüntülerinin işlenmesi
* Görüntü ve maske eşleştirme
* Veri artırma teknikleri
* PyTorch ile derin öğrenme modeli geliştirme
* GPU üzerinde model eğitimi
* IoU ve Dice metrikleriyle model değerlendirme
* Dense CRF ile segmentasyon sonuçlarının iyileştirilmesi

konularında deneyim kazanılmıştır.

## 👩‍💻 Geliştirici

**Damla Tatlıcan**

Adli Bilişim Mühendisliği mezunu.

İlgi alanları:

* Artificial Intelligence
* Deep Learning
* Computer Vision
* Machine Learning
* Image Processing
* Cybersecurity

---

⭐ Bu proje, uydu görüntülerinden GES alanlarının otomatik olarak tespit edilmesi üzerine gerçekleştirilmiş bir **derin öğrenme ve görüntü segmentasyonu çalışmasıdır.**
