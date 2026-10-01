# 🗺️ OpenManus Yerel Model Optimizasyonu & Fork Yol Haritası

Bu doküman, OpenManus çerçevesini **yerel / LAN Ollama** modelleri ile tam uyumlu, kararlı ve yüksek performanslı hale getirmek için yürütülecek geliştirme ve test planını içerir.

---

## 1. Fork & Depo Yapılandırması

* **Upstream:** `https://github.com/FoundationAgents/OpenManus.git` (535+ commit, en güncel mimari)
* **Geliştirici / Fork:** `git@github.com:onkanat/OpenManus.git`
* **Aktif Çalışma Dalı:** `local-ollama-dev` (yerel denemeler ve testler bu dalda toplanır)
* **Yerel Git Sunucusu (Yedek):** `pi2b01.local:/mnt/dt30/git_repo/OpenManus.git`

---

## 2. LAN Ollama Test Matrisi (`192.168.1.26` - 2x RTX 4060 Ti 16GB)

Farklı parametre büyüklükleri ve mimarilerdeki yerel modellerle OpenManus'un ReAct döngüsü, JSON şema uyumu ve araç seçimi sınanacaktır:

| Seviye | Model Adı | Parametre | Mimari / Aile | Test Odak Noktası |
| :--- | :--- | :---: | :--- | :--- |
| **Hafif (Light)** | `ornith-1.5:9b` | 9.0B | Qwen3.5 | Temel ReAct hızı, JSON şema başarısı (Şu an doğrulanmış) |
| **Giriş-Orta** | `gemma4:latest` | 8.0B | Gemma 4 | Çok dilli anlama, Türkçe prompt performansı |
| **Orta (Mid)** | `gemma4:12b-it-qat` | 11.9B | Gemma 4 QAT | Tool seçimi hassasiyeti, bağlam tutarlılığı |
| **Ağır-MoE** | `gemma4:26b-a4b-it-qat` | 25.2B | Gemma 4 MoE | Çok adımlı planlama yeteneği, karmaşık kod üretimi |
| **Üst Seviye (Heavy)**| `ornith:35b-q4_K_M` | 34.7B | Qwen3.5 MoE | SWE / Çoklu araç kullanımı, minimum halüsinasyon |

---

## 3. İncelenecek ve Ölçülecek Metrikler

1. **Token Üretim & Yanıt Süresi (Latency / Throughput):**
   - TTFT (Time to First Token) ve tokens/second (t/s) ölçümü.
   - Kümülatif bağlam (context window) büyüdükçe (10K - 30K token) yerel modelin tepki süreleri.
2. **Tool-Call / JSON Şema Sadakati:**
   - Modelin beklenen JSON formatını bozup bozmadığı.
   - 0 tools döngüsüne (sonsuz diyalog tuzağı) girip girmediği.
3. **Görev Bitirme (Termination Accuracy):**
   - Görev tamamlandığında `terminate` aracını çağırma kararlılığı.

---

## 4. Yerel Modellere Özel Prompt Geliştirme Stratejisi

OpenManus varsayılanda Claude-3.7 ve GPT-4o gibi büyük ticari modellerin varsayımlarıyla yazılmıştır. Yerel modeller için şu iyileştirmeler `app/prompt/` altına eklenecektir:

1. **Sonsuz Döngü Kırıcı (Loop Breaker):**
   - Eğer model art arda 2 adım araç seçmezse ve kullanıcıdan yeni girdi beklerse, sistem promptu modele *"Eğer elinde görev varsa varsayım yapma, terminate aracıyla bitir veya bir tool çağır"* şeklinde net direktif vermelidir.
2. **Kompakt Sistem Promptu:**
   - ~2000 tokenlik devasa sistem promptları yerel 8B-12B modellerin dikkat mekanizmasını (attention) dağıtabilir. Yerel modeller için hafifletilmiş, kuralları daha net bir `LOCAL_SYSTEM_PROMPT` şablonu oluşturulacaktır.
3. **Structured Output / JSON Modu Zorlaması:**
   - Ollama OpenAI uyumluluk katmanında `response_format={"type": "json_object"}` veya kesin tool deklarasyonları.

---

## 5. Doğrulama Senaryoları (Test Suite)

- **Test A (Basit Araç Kullanımı):** `PythonExecute` ile matematik ve string işleme.
- **Test B (Web Veri Çekme & Özetleme):** GitHub sayfası veya teknik doküman taraması.
- **Test C (Dosya İşlemleri):** `workspace/` altında dosya oluşturma, okuma, düzenleme.
- **Test D (Hata Kurtarma):** Hatalı URL veya çöken bir kod verildiğinde modelin toparlanıp alternatif üretmesi.

---

## 6. Upstream Katkı (PR) Aşamaları

1. **Faz 1 (Hemen):** `DaytonaSettings` API anahtarı zorunluluğunu kaldıran temiz bugfix PR'ı.
2. **Faz 2 (Testler Sonrası):** `config.toml` içine yerel Ollama / LAN sağlayıcı şablonunun eklenmesi ve yerel model prompt optimizasyonlarının PR olarak sunulması.
