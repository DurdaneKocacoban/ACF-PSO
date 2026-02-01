# ACF-PSO

Examined sboxes used in Advanced Composite Fitness Particle Swarm Optimization: Achieving Theoretical Maximum Nonlinearity for S-box Design 


## 📋 İçindekiler
- [Genel Bakış](#genel-bakış)
- [Veri Yapısı](#veri-yapısı)
- [Deney Türleri](#deney-türleri)
- [Dosya Formatları](#dosya-formatları)
- [Kullanım](#kullanım)

## 🔍 Genel Bakış

Bu repository, [projenizin kısa açıklaması] için yapılan deneylerin sonuçlarını içermektedir. Toplam 4 farklı deney kategorisi bulunmaktadır.

## 📁 Veri Yapısı
```
data/
├── main_experiments/      # Ana deneyler (30 run × 3 dosya)
├── weight_sensitivity/    # Ağırlık duyarlılık analizi (3 ağırlık × 5 run × 3 dosya)
├── ablation/             # Ablation çalışması (5 kademe × 5 run × 3 dosya)
└── multiple_runs/        # Çoklu çalıştırma testleri (her run 10 iterasyon)
```

## 🧪 Deney Türleri

### 1. Ana Deneyler (`main_experiments/`)
- **Toplam Run Sayısı:** 30
- **Run Başına Dosya:** 3 txt dosyası
- **Toplam Dosya:** 90
- **Amaç:** [Ana deneyinizin amacı]

#### Dosya İsimlendirme
```
run_001/
  ├── output_1.txt  # [Dosyanın içeriği]
  ├── output_2.txt  # [Dosyanın içeriği]
  └── output_3.txt  # [Dosyanın içeriği]
```

### 2. Ağırlık Duyarlılık Analizi (`weight_sensitivity/`)
- **Ağırlık Değerleri:** 3 farklı (örn: 0.1, 0.5, 1.0)
- **Ağırlık Başına Run:** 5
- **Run Başına Dosya:** 3 txt dosyası
- **Toplam Dosya:** 45
- **Amaç:** Farklı ağırlık parametrelerinin model performansına etkisini analiz etmek

#### Klasör Yapısı
```
weight_0.1/
  ├── run_001/
  │   ├── output_1.txt
  │   ├── output_2.txt
  │   └── output_3.txt
  └── ... (run_005'e kadar)
weight_0.5/
  └── ... (aynı yapı)
weight_1.0/
  └── ... (aynı yapı)
```

### 3. Ablation Çalışması (`ablation/`)
- **Kademe Sayısı:** 5
- **Kademe Başına Run:** 5
- **Run Başına Dosya:** 3 txt dosyası
- **Toplam Dosya:** 75
- **Amaç:** Model bileşenlerinin katkısını sistematik olarak değerlendirmek

#### Kademeler
- **Stage 1:** [Açıklama]
- **Stage 2:** [Açıklama]
- **Stage 3:** [Açıklama]
- **Stage 4:** [Açıklama]
- **Stage 5:** [Açıklama]

### 4. Çoklu Çalıştırma Testleri (`multiple_runs/`)
- **Çalışma Şekli:** Her run ardışık 10 kez çalıştırılır
- **İterasyon Başına Dosya:** 1 txt dosyası
- **Amaç:** Model kararlılığını ve tekrarlanabilirliğini test etmek

#### Dosya Formatı
```
run_001/
  ├── iteration_01.txt
  ├── iteration_02.txt
  └── ... (iteration_10'a kadar)
```

## 📄 Dosya Formatları

Her txt dosyası şu bilgileri içerir:
- [Dosya içeriğinin açıklaması]
- [Metriklerin listesi]
- [Özel formatlar]

**Örnek:**
```
Metric 1: 0.95
Metric 2: 0.87
Timestamp: 2024-02-01 10:30:45
...
```

## 🚀 Kullanım

### Veri Okuma
```python
# Örnek kod: Ana deney verilerini okuma
import os

def read_experiment(run_id):
    base_path = f"data/main_experiments/run_{run_id:03d}"
    results = {}
    for i in range(1, 4):
        with open(f"{base_path}/output_{i}.txt", 'r') as f:
            results[f'output_{i}'] = f.read()
    return results

# Run 1'i oku
data = read_experiment(1)
```

### Analiz
```python
# Tüm weight sensitivity sonuçlarını karşılaştır
weights = [0.1, 0.5, 1.0]
for w in weights:
    print(f"Weight {w} sonuçları analiz ediliyor...")
    # Analiz kodu
```

## 📊 Özet İstatistikler

| Deney Türü | Run Sayısı | Dosya/Run | Toplam Dosya |
|------------|-----------|-----------|--------------|
| Ana Deneyler | 30 | 3 | 90 |
| Weight Sensitivity | 15 (3×5) | 3 | 45 |
| Ablation | 25 (5×5) | 3 | 75 |
| Multiple Runs | Değişken | 10 | Değişken |

**Toplam Dosya Sayısı:** 210+

## 🔧 Gereksinimler
```
python >= 3.8
numpy >= 1.20.0
pandas >= 1.3.0
matplotlib >= 3.4.0
```

## 📝 Notlar

- Her run bağımsız olarak çalıştırılmıştır
- Random seed değerleri her run için farklıdır
- Detaylı konfigürasyon bilgileri `config/` klasöründe bulunabilir

## 👥 Katkıda Bulunanlar

[İsim] - [Email]

## 📄 Lisans

[Lisans bilgisi]
