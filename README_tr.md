<p align="center">
  <img src="assets/logo.jpg" width="200"/>
</p>

[English](README.md) | [中文](README_zh.md) | [한국어](README_ko.md) | [日本語](README_ja.md) | Türkçe

[![GitHub stars](https://img.shields.io/github/stars/FoundationAgents/OpenManus?style=social)](https://github.com/FoundationAgents/OpenManus/stargazers)
&ensp;
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) &ensp;
[![Discord Follow](https://dcbadge.vercel.app/api/server/DYn29wFk9z?style=flat)](https://discord.gg/DYn29wFk9z)
[![Demo](https://img.shields.io/badge/Demo-Hugging%20Face-yellow)](https://huggingface.co/spaces/lyh-917/OpenManusDemo)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.15186407.svg)](https://doi.org/10.5281/zenodo.15186407)

# 👋 OpenManus

Manus harika bir sistem, ancak OpenManus herhangi bir fikri bir *Davet Kodu (Invite Code)* gerekmeksizin hayata geçirebilir 🛫!

Ekip üyelerimiz [@Xinbing Liang](https://github.com/mannaandpoem) ve [@Jinyu Xiang](https://github.com/XiangJinyu) (çekirdek yazarlar) ile birlikte [@Zhaoyang Yu](https://github.com/MoshiQAQ), [@Jiayi Zhang](https://github.com/didiforgithub) ve [@Sirui Hong](https://github.com/stellaHSR), [@MetaGPT](https://github.com/geekan/MetaGPT) ekibinden gelmektedir. Prototip 3 saat içinde hayata geçirilmiştir ve aktif olarak geliştirilmeye devam etmektedir!

Bu sade ve güçlü bir uygulamadır; bu nedenle her türlü öneriyi, katkıyı ve geri bildirimi memnuniyetle karşılıyoruz!

OpenManus ile kendi yapay zeka ajanınızın keyfini çıkarın!

Ayrıca, UIUC ve OpenManus araştırmacıları tarafından ortaklaşa geliştirilen, LLM ajanları için pekiştirmeli öğrenme (RL) tabanlı (GRPO gibi) ince ayar (tuning) yöntemlerine adanmış açık kaynaklı [OpenManus-RL](https://github.com/OpenManus/OpenManus-RL) projesini duyurmaktan heyecan duyuyoruz.

## Proje Demosu

<video src="https://private-user-images.githubusercontent.com/61239030/420168772-6dcfd0d2-9142-45d9-b74e-d10aa75073c6.mp4?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDEzMTgwNTksIm5iZiI6MTc0MTMxNzc1OSwicGF0aCI6Ii82MTIzOTAzMC80MjAxNjg3NzItNmRjZmQwZDItOTE0Mi00NWQ5LWI3NGUtZDEwYWE3NTA3M2M2Lm1wND9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTAzMDclMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwMzA3VDAzMjIzOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTdiZjFkNjlmYWNjMmEzOTliM2Y3M2VlYjgyNDRlZDJmOWE3NWZhZjE1MzhiZWY4YmQ3NjdkNTYwYTU5ZDA2MzYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.UuHQCgWYkh0OQq9qsUWqGsUbhG3i9jcZDAMeHjLt5T4" data-canonical-src="https://private-user-images.githubusercontent.com/61239030/420168772-6dcfd0d2-9142-45d9-b74e-d10aa75073c6.mp4?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDEzMTgwNTksIm5iZiI6MTc0MTMxNzc1OSwicGF0aCI6Ii82MTIzOTAzMC80MjAxNjg3NzItNmRjZmQwZDItOTE0Mi00NWQ5LWI3NGUtZDEwYWE3NTA3M2M2Lm1wND9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTAzMDclMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwMzA3VDAzMjIzOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTdiZjFkNjlmYWNjMmEzOTliM2Y3M2VlYjgyNDRlZDJmOWE3NWZhZjE1MzhiZWY4YmQ3NjdkNTYwYTU5ZDA2MzYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.UuHQCgWYkh0OQq9qsUWqGsUbhG3i9jcZDAMeHjLt5T4" controls="controls" muted="muted" class="d-block rounded-bottom-2 border-top width-fit" style="max-height:640px; min-height: 200px"></video>

## Kurulum

İki farklı kurulum yöntemi sunuyoruz. Daha hızlı kurulum ve modern bağımlılık yönetimi için **Yöntem 2 (uv kullanımı)** önerilir.

### Yöntem 1: Conda Kullanarak

1. Yeni bir conda sanal ortamı oluşturun:

```bash
conda create -n open_manus python=3.12
conda activate open_manus
```

2. Depoyu klonlayın:

```bash
git clone https://github.com/FoundationAgents/OpenManus.git
cd OpenManus
```

3. Bağımlılıkları yükleyin:

```bash
pip install -r requirements.txt
```

### Yöntem 2: uv Kullanarak (Önerilen)

1. uv paket yöneticisini kurun (Hızlı bir Python paket çözücüsü ve yükleyicisi):

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

2. Depoyu klonlayın:

```bash
git clone https://github.com/FoundationAgents/OpenManus.git
cd OpenManus
```

3. Yeni bir sanal ortam oluşturun ve etkinleştirin:

```bash
uv venv --python 3.12
source .venv/bin/activate  # Unix/macOS için
# Veya Windows için:
# .venv\Scripts\activate
```

4. Bağımlılıkları yükleyin:

```bash
uv pip install -r requirements.txt
```

### Tarayıcı Otomasyonu

OpenManus, varsayılan bir MCP sunucusu olarak Browser Use CLI 3.0'ı başlatır:

```bash
uvx browser-use --cli-mcp
```

`uvx`, Browser Use ve hızla güncellenen bağımlılıklarını OpenManus ortamından izole tutar. Ajan, standart Browser Use becerisini ve yerel `browser_exec` ile `browser_screenshot` araçlarını kullanır.

Yerel mod Chrome veya Chromium'a otomatik olarak bağlanır ve herhangi bir API anahtarı gerektirmez. Tanılama yapmak veya Chromium'u kurmak için:

```bash
uvx browser-use --doctor
uvx browser-use install
```

İzole bir Browser Use Cloud tarayıcısı kullanmak için OpenManus'u başlatmadan önce kimlik doğrulaması yapın:

```bash
export BROWSER_USE_API_KEY="bu_..."
```

Mevcut tarayıcılar `BU_CDP_URL`, `BU_CDP_WS` veya `BU_NAME` ile seçilebilir. Varsayılan Browser Use MCP sunucusunu devre dışı bırakmak için `OPENMANUS_DISABLE_BROWSER_USE=1` ortam değişkenini tanımlayabilirsiniz.

BrowserGym için Playwright tarayıcısının kurulması gereklidir:

```bash
playwright install
```

## Yapılandırma

OpenManus, kullandığı LLM API'leri için yapılandırma gerektirir. Ayarlarınızı tamamlamak için şu adımları izleyin:

1. `config` dizini altında bir `config.toml` dosyası oluşturun (örnek dosyayı kopyalayabilirsiniz):

```bash
cp config/config.example.toml config/config.toml
```

2. `config/config.toml` dosyasını düzenleyerek API anahtarlarınızı ve tercih ettiğiniz ayarları ekleyin:

```toml
# Genel LLM Yapılandırması (OpenAI / Yerel Ollama / Anthropic vb.)
[llm]
model = "gpt-4o"
base_url = "https://api.openai.com/v1"
api_key = "sk-..."  # Gerçek API anahtarınızı buraya yazın
max_tokens = 4096
temperature = 0.0

# Görsel modeller için isteğe bağlı yapılandırma
[llm.vision]
model = "gpt-4o"
base_url = "https://api.openai.com/v1"
api_key = "sk-..."
```

> **Yerel Ollama Kullanımı (Örnek):**
> ```toml
> [llm]
> model = "ornith-1.5:9b"
> base_url = "http://localhost:11434/v1"
> api_key = "ollama"
> max_tokens = 4096
> temperature = 0.0
> ```

## Hızlı Başlangıç

OpenManus'u tek satırla çalıştırın:

```bash
python main.py
```

Ardından terminale gerçekleştirmek istediğiniz görevi yazın!

Komut satırından doğrudan komut vermek için:
```bash
python main.py --prompt "Google ana sayfasını ziyaret et ve başlığı oku."
```

MCP araçları sürümü için:
```bash
python run_mcp.py
```

Çoklu ajan iş akışları için:
```bash
python run_flow.py
```

### Özel Çoklu Ajan Ekleme

Genel OpenManus ajanının yanı sıra, veri analizi ve görselleştirme görevlerine uygun **DataAnalysis Agent** entegre edilmiştir. Bu ajanı `config.toml` içindeki `runflow` bölümünden etkinleştirebilirsiniz:

```toml
# run-flow için isteğe bağlı yapılandırma
[runflow]
use_data_analysis_agent = true     # Varsayılan olarak kapalıdır, aktifleştirmek için true yapın
```
İlgili bağımlılıkların kurulumu için: [Detaylı Kurulum Kılavuzu](app/tool/chart_visualization/README.md##Installation)

## Nasıl Katkıda Bulunabilirsiniz?

Her türlü dostça öneri ve katkıyı memnuniyetle karşılıyoruz! Sorun bildirimi (issue) açabilir veya pull request (PR) gönderebilirsiniz.

Doğrudan iletişim için: @mannaandpoem 📧 e-posta: mannaandpoem@gmail.com

**Not**: Bir pull request göndermeden önce lütfen pre-commit aracını kullanarak değişikliklerinizi denetleyin: `pre-commit run --all-files`.

## Topluluk

Feishu üzerindeki iletişim grubumuza katılın ve deneyimlerinizi diğer geliştiricilerle paylaşın!

<div align="center" style="display: flex; gap: 20px;">
    <img src="assets/community_group.jpg" alt="OpenManus Topluluk Grubu" width="300" />
</div>

## Yıldız Geçmişi

[![Star History Chart](https://api.star-history.com/svg?repos=FoundationAgents/OpenManus&type=Date)](https://star-history.com/#FoundationAgents/OpenManus&Date)

## Destekleyenler & Sponsorlar
Hesaplama kaynakları desteği için [PPIO](https://ppinfra.com/user/register?invited_by=OCPKCN&utm_source=github_openmanus&utm_medium=github_readme&utm_campaign=link)'ya teşekkürler.
> PPIO: En uygun fiyatlı ve kolay entegre edilebilir MaaS ve GPU bulut çözümü.

## Teşekkürler

Bu projeye temel destek sağlayan [anthropic-computer-use](https://github.com/anthropics/anthropic-quickstarts/tree/main/computer-use-demo), [browser-use](https://github.com/browser-use/browser-use) ve [crawl4ai](https://github.com/unclecode/crawl4ai) projelerine teşekkür ederiz!

Ayrıca [AAAJ](https://github.com/metauto-ai/agent-as-a-judge), [MetaGPT](https://github.com/geekan/MetaGPT), [OpenHands](https://github.com/All-Hands-AI/OpenHands) ve [SWE-agent](https://github.com/SWE-agent/SWE-agent) ekiplerine minnettarız.

Hugging Face demo alanı desteği için stepfun (阶跃星辰) ekibine teşekkürler.

OpenManus, MetaGPT topluluğundan gelen katkıcılar tarafından inşa edilmiştir. Tüm ajan topluluğuna büyük teşekkürler!

## Alıntı

```bibtex
@misc{openmanus2025,
  author = {Xinbing Liang and Jinyu Xiang and Zhaoyang Yu and Jiayi Zhang and Sirui Hong and Sheng Fan and Xiao Tang and Bang Liu and Yuyu Luo and Chenglin Wu},
  title = {OpenManus: An open-source framework for building general AI agents},
  year = {2025},
  publisher = {Zenodo},
  doi = {10.5281/zenodo.15186407},
  url = {https://doi.org/10.5281/zenodo.15186407},
}
```
