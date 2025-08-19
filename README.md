# 🔧 Fine-Tuning Gemma 3 (270M) with Kodla Data

Bu proje, **Gemma 3 - 270M** küçük dil modeli üzerinde **Kodla kanalına özel görevleri yerine getirebilen** bir yapay zeka modelini fine-tuning (ince ayar) yöntemiyle eğitmek amacıyla hazırlanmıştır.

---

## 📌 Projenin Amacı

YouTube’daki Kodla kanalında görev alan içerik yöneticilerinin görevlerini kolaylaştırmak için eğitilen bu model:

- Kanalda hangi videonun hangi oynatma listesine eklenmesi gerektiğini,
- Mevcut oynatma listelerini,
- Video başlığı ve açıklama yazımı gibi içerik önerilerini
kendi başına cevaplayabilir hale gelir.

---

## ⚙️ Kullanılan Model

- **Model:** `gemma-3b` base modeli (270M parametreli sürüm)
- **Kütüphane:** [Unsloth](https://github.com/unslothai/unsloth) (hızlı fine-tuning için)
- **Format:** GGUF (`F16` quantized)

---

## 📂 Eğitim Verisi

Veriler `kodla_data.json` dosyasındadır ve `conversations` formatında yapılandırılmıştır:

```json
{
  "conversations": [
    { "role": "system", "content": "Sen Kodla kanalında çalışan bir içerik yöneticisi asistansın." },
    { "role": "user", "content": "Kodla kanalında kaç tane playlist bulunuyor?" },
    { "role": "assistant", "content": "Kodla kanalında 5 playlist var: ..." }
  ]
}
```

Veriler kontrollü dil ve tekil görevli sorularla hazırlanmıştır. Toplam 20+ farklı senaryo yer almaktadır.

---

## 🏋️ Eğitim Süreci

1. Ortam Google Colab üzerinde T4 GPU ile çalıştırılır.
2. Model `unsloth` kütüphanesiyle yüklenir (`2048` bağlam uzunluğu ile).
3. Veriler tokenize edilip `SFTTrainer` ile eğitilir.
4. Eğitim 2-3 epoch arası yapılır, kayıp (`loss`) değerleri izlenir.
5. Eğitim sonrası model `.gguf` formatında dışa aktarılır.

---

## 🧠 Modelfile

Modelin inference (çıktı üretimi) için kullanımı aşağıdaki `Modelfile` ile yapılır:

```
FROM ./model.F16.gguf

PARAMETER temperature 0.5
PARAMETER top_p 0.8
PARAMETER top_k 64
PARAMETER num_ctx 2048
PARAMETER stop "<end_of_turn>"
```

---

## 💡 Örnek Kullanım

Model şu tarz sorulara otomatik ve tutarlı yanıtlar verebilir:

- “Kodla kanalında kaç tane oynatma listesi var?”
- “Yeni teknoloji hakkında video çektim, hangi listeye koymalıyım?”
- “Thumbnail’de hangi renkler tercih edilmeli?”

---

## 📦 Çıktı

Eğitilen model:
- `model.F16.gguf` adıyla kaydedildi.
- Mobil cihazlarda dahi kullanılabilecek kadar küçüktür.
- Tokenizer bilgileriyle birlikte paketlendi.

---

## 📎 Notlar

- Bu proje eğitim amaçlıdır.
- Model küçük olduğundan karmaşık görevlerde değil, spesifik görevlerde (Kodla içeriği gibi) başarılı çalışır.
- Veri seti güncellendikçe model yeniden eğitilebilir.

---

## 🧠 Teşekkürler

Modelin hızlı fine-tuning’i için [Unsloth](https://github.com/unslothai/unsloth) kütüphanesi kullanılmıştır.