# Seviye 4 — 6 Dirençli Seri-Paralel DC Devre

## 1) Devrenin topolojisi

Sırayla: **R1** seri → **R2 ∥ R3** paralel → **R4** seri → **R5 ∥ R6** paralel. İki ayrı paralel grup, aralarında seri bir direnç ile bağlanmıştır.

```
 (+)──[ R1 ]──┬──[ R2 ]──┬──[ R4 ]──┬──[ R5 ]──┬──(−)
              │          │          │          │
              └──[ R3 ]──┘          └──[ R6 ]──┘
```

## 2) Verilen değerler

| Büyüklük | Değer |
|---|---|
| Kaynak gerilimi **V** | 30 V |
| R1 | 1 kΩ |
| R2 | 8 kΩ |
| R3 | 8 kΩ |
| R4 | 3 kΩ |
| R5 | 6 kΩ |
| R6 | 3 kΩ |

> **Birim notu:** Bütün dirençleri **kΩ**, kaynağı **V** cinsinden yazıyoruz. Volt'u kΩ'a bölünce sonuç doğrudan **mA** çıkar (çünkü V / kΩ = mA). Gerilim (V) × akım (mA) çarpımı ise **mW** verir. Böylece hiçbir yerde 1000 ile çarpma/bölme yapmaya gerek kalmaz.
>
> Sayılar 4 ondalık haneye yuvarlandı; toplamlarda son hanede çok küçük farklar görebilirsiniz, bu yuvarlamadandır.

## 3) Eşdeğer direnç — adım adım

Kural: **en içteki / en küçük paralel gruptan başla**, onu tek bir dirence indir, sonra dışa doğru ilerle. Seri olanlar en son toplanır.

**Adım 1.** **R23 = (R2 · R3) / (R2 + R3)**  (iki direnç paralel → çarpım/toplam)

- Çarpım: 8 · 8 = 64
- Toplam: 8 + 8 = 16
- R23 = 64 / 16 = **4 kΩ**

**Adım 2.** **R56 = (R5 · R6) / (R5 + R6)**  (iki direnç paralel → çarpım/toplam)

- Çarpım: 6 · 3 = 18
- Toplam: 6 + 3 = 9
- R56 = 18 / 9 = **2 kΩ**

**Adım 3.** **R_eş = R1 + R23 + R4 + R56**  (seri bağlı, doğrudan toplanır)

R_eş = 1 + 4 + 3 + 2 = **10 kΩ**

➡️ **Devrenin eşdeğer direnci: R_eş = 10 kΩ**

## 4) Toplam akım (Ohm kanunu)

Kaynak, devrenin tamamını tek bir R_eş direnci gibi görür:

> I_toplam = V / R_eş = 30 V / 10 kΩ = **3 mA**

Volt'u kΩ'a böldüğümüz için sonuç doğrudan mA çıktı.

## 5) Her direncin gerilimi ve akımı

Hatırlatma: **seri** bağlı elemanlardan *aynı akım* geçer; **paralel** bağlı kolların *uçlarındaki gerilim aynıdır*.

- **R1** üzerinden 3 mA geçer → V_1 = I · R = 3 · 1 = **3 V**
- **R23** grubunun uçlarındaki gerilim: V = I · R = 3 · 4 = **12 V**
  - Bu paralel grubun her kolunda aynı **12 V** vardır:
    - **R2**: I = V / R = 12 / 8 = **1.5 mA**  (gerilimi 12 V)
    - **R3**: I = V / R = 12 / 8 = **1.5 mA**  (gerilimi 12 V)
- **R4** üzerinden 3 mA geçer → V_4 = I · R = 3 · 3 = **9 V**
- **R56** grubunun uçlarındaki gerilim: V = I · R = 3 · 2 = **6 V**
  - Bu paralel grubun her kolunda aynı **6 V** vardır:
    - **R5**: I = V / R = 6 / 6 = **1 mA**  (gerilimi 6 V)
    - **R6**: I = V / R = 6 / 3 = **2 mA**  (gerilimi 6 V)

## 6) Özet tablo

| Direnç | R (kΩ) | Gerilim V (V) | Akım I (mA) | Güç P = V·I (mW) |
|---|---|---|---|---|
| R1 | 1 | 3 | 3 | 9 |
| R2 | 8 | 12 | 1.5 | 18 |
| R3 | 8 | 12 | 1.5 | 18 |
| R4 | 3 | 9 | 3 | 27 |
| R5 | 6 | 6 | 1 | 6 |
| R6 | 3 | 6 | 2 | 12 |

## 7) Kontroller

### 7.1 KVL — gerilim düşümleri toplamı

- **Ana seri kol:** V(R1) + V(R23) + V(R4) + V(R56) = 3 + 12 + 9 + 6 = **30 V** = kaynak gerilimi (30 V) ✔

### 7.2 KCL — düğüm akımları toplamı

- **R23 düğümü:** I(R2) + I(R3) = 1.5 + 1.5 = **3 mA** = gruba giren akım (3 mA) ✔
- **R56 düğümü:** I(R5) + I(R6) = 1 + 2 = **3 mA** = gruba giren akım (3 mA) ✔

### 7.3 Güç kontrolü

- Dirençlerin güçleri toplamı: **90 mW**
- Kaynağın verdiği güç: P = V · I_toplam = 30 · 3 = **90 mW**
- İkisi eşit ✔ (enerji korunumu sağlanıyor)

## 8) Simülatörde (EveryCircuit / Proto / online araç) beklenen değerler

Devreyi kurduktan sonra ölçtüğünüz değerler bu tabloyla birebir aynı çıkmalı:

| Ölçülecek | Beklenen değer |
|---|---|
| Eşdeğer direnç R_eş | 10 kΩ |
| Kaynaktan çekilen toplam akım | 3 mA |
| R1 → gerilim / akım | 3 V / 3 mA |
| R2 → gerilim / akım | 12 V / 1.5 mA |
| R3 → gerilim / akım | 12 V / 1.5 mA |
| R4 → gerilim / akım | 9 V / 3 mA |
| R5 → gerilim / akım | 6 V / 1 mA |
| R6 → gerilim / akım | 6 V / 2 mA |

## 9) YouTube video başlığı

> **6 Dirençli Seri-Paralel DC Devre Çözümü by ______________**

*(Boşluğa kendi isminizi yazın.)*
