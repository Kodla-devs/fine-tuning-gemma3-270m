# Gemma 3 270M Fine-Tuning Projesi

Bu proje, **Google Gemma 3 (270M parametreli)** modeli üzerinde **fine-tuning** yaparak özelleştirilmiş bir yapay zeka modeli geliştirmeyi amaçlamaktadır.  
Model, telefonda bile çalışabilecek kadar küçük olup, ince ayar sayesinde belirli görevlerde uzmanlaşabilmektedir.

---

## 📂 Proje Dosyaları

- **`gemma3-fine-tuning.ipynb`**  
  Jupyter Notebook dosyası. Fine-tuning sürecini adım adım gösterir:
  - Veri setinin yüklenmesi ve dönüştürülmesi  
  - Eğitim parametrelerinin ayarlanması  
  - Modelin yeniden kaydedilmesi (GGUF formatında)  
  - Test aşaması

- **`kodla_data.json`**  
  Kodla YouTube kanalındaki playlist verilerini içerir.  
  Bu veri seti, kanal içeriklerini sınıflandırmak ve yapay zekaya içerik yönetimi konusunda ince ayar yapmak için kullanılır.  
  Playlistler:  
  1. Kodla Deney  
  2. Kodla Keşfet  
  3. Kodla Analiz  
  4. Kodla Atölye  
  5. Kodla Gündem  

---

## 🚀 Kullanım

1. Notebook’u aç:  
   ```bash
   jupyter notebook gemma3-fine-tuning.ipynb
   ```

2. Eğitim adımlarını sırayla çalıştır:  
   - Veri yükleme  
   - Dönüştürme  
   - Fine-tuning  
   - Modeli kaydetme  

3. Eğitilen modeli test et ve kendi verinle çalıştır.  

---

## 🎯 Örnek Senaryolar

- **Şirket içi bilgi asistanı**: Tüm prosedür ve iş süreçlerini modele öğreterek çalışanların doğal dil ile bilgiye ulaşmasını sağla.  
- **Tarihsel karakter modeli**: Örneğin Mimar Sinan verileriyle eğitilmiş, onun dönemine uygun cevaplar veren bir yapay zeka oluştur.  
- **YouTube içerik yöneticisi**: `kodla_data.json` verisi ile kanal playlistlerini bilen ve doğru kategorilere yönlendirme yapan bir yapay zeka asistanı geliştir.

---

## 📌 Notlar

- Fine-tuning, modeli sıfırdan eğitmek yerine mevcut bilgi üzerine özel veriyle ince ayar yapar.  
- Küçük modeller (Gemma 3 270M gibi) telefonlarda dahi çalışabilir.  
- Eğitimden sonra model GGUF formatında kaydedilip Ollama veya benzeri ortamlarda kullanılabilir.

---

## 📜 Lisans

Bu proje eğitim ve araştırma amaçlı hazırlanmıştır.
