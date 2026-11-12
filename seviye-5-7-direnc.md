# Seviye 5 — 7 Dirençli Seri-Paralel DC Devre

## 1) Devrenin topolojisi

Sırayla: **R1** seri → **R2 ∥ R3 ∥ R4** üçlü paralel → **R5** seri → **R6 ∥ R7** paralel.

```
 (+)──[ R1 ]──┬──[ R2 ]──┬──[ R5 ]──┬──[ R6 ]──┬──(−)
              ├──[ R3 ]──┤          │          │
              └──[ R4 ]──┘          └──[ R7 ]──┘
```

## 2) Verilen değerler

| Büyüklük | Değer |
|---|---|
| Kaynak gerilimi **V** | 48 V |
| R1 | 2 kΩ |
| R2 | 6 kΩ |
| R3 | 3 kΩ |
| R4 | 2 kΩ |
| R5 | 5 kΩ |
| R6 | 4 kΩ |
| R7 | 4 kΩ |

> **Birim notu:** Bütün dirençleri **kΩ**, kaynağı **V** cinsinden yazıyoruz. Volt'u kΩ'a bölünce sonuç doğrudan **mA** çıkar (çünkü V / kΩ = mA). Gerilim (V) × akım (mA) çarpımı ise **mW** verir. Böylece hiçbir yerde 1000 ile çarpma/bölme yapmaya gerek kalmaz.
>
> Sayılar 4 ondalık haneye yuvarlandı; toplamlarda son hanede çok küçük farklar görebilirsiniz, bu yuvarlamadandır.

## 3) Eşdeğer direnç — adım adım

Kural: **en içteki / en küçük paralel gruptan başla**, onu tek bir dirence indir, sonra dışa doğru ilerle. Seri olanlar en son toplanır.

**Adım 1.** **1/R234 = 1/R2 + 1/R3 + 1/R4**  (ikiden fazla paralel → ters toplam)

- 1/R234 = 1/6 + 1/3 + 1/2
- 1/R234 ≈ 0.16667 + 0.33333 + 0.5 = 1  (1/kΩ)
- R234 = 1 / 1 = **1 kΩ**

**Adım 2.** **R67 = (R6 · R7) / (R6 + R7)**  (iki direnç paralel → çarpım/toplam)

- Çarpım: 4 · 4 = 16
- Toplam: 4 + 4 = 8
- R67 = 16 / 8 = **2 kΩ**

**Adım 3.** **R_eş = R1 + R234 + R5 + R67**  (seri bağlı, doğrudan toplanır)

R_eş = 2 + 1 + 5 + 2 = **10 kΩ**

➡️ **Devrenin eşdeğer direnci: R_eş = 10 kΩ**

## 4) Toplam akım (Ohm kanunu)

Kaynak, devrenin tamamını tek bir R_eş direnci gibi görür:

> I_toplam = V / R_eş = 48 V / 10 kΩ = **4.8 mA**

Volt'u kΩ'a böldüğümüz için sonuç doğrudan mA çıktı.

## 5) Her direncin gerilimi ve akımı

Hatırlatma: **seri** bağlı elemanlardan *aynı akım* geçer; **paralel** bağlı kolların *uçlarındaki gerilim aynıdır*.

- **R1** üzerinden 4.8 mA geçer → V_1 = I · R = 4.8 · 2 = **9.6 V**
- **R234** grubunun uçlarındaki gerilim: V = I · R = 4.8 · 1 = **4.8 V**
  - Bu paralel grubun her kolunda aynı **4.8 V** vardır:
    - **R2**: I = V / R = 4.8 / 6 = **0.8 mA**  (gerilimi 4.8 V)
    - **R3**: I = V / R = 4.8 / 3 = **1.6 mA**  (gerilimi 4.8 V)
    - **R4**: I = V / R = 4.8 / 2 = **2.4 mA**  (gerilimi 4.8 V)
- **R5** üzerinden 4.8 mA geçer → V_5 = I · R = 4.8 · 5 = **24 V**
- **R67** grubunun uçlarındaki gerilim: V = I · R = 4.8 · 2 = **9.6 V**
  - Bu paralel grubun her kolunda aynı **9.6 V** vardır:
    - **R6**: I = V / R = 9.6 / 4 = **2.4 mA**  (gerilimi 9.6 V)
    - **R7**: I = V / R = 9.6 / 4 = **2.4 mA**  (gerilimi 9.6 V)

## 6) Özet tablo

| Direnç | R (kΩ) | Gerilim V (V) | Akım I (mA) | Güç P = V·I (mW) |
|---|---|---|---|---|
| R1 | 2 | 9.6 | 4.8 | 46.08 |
| R2 | 6 | 4.8 | 0.8 | 3.84 |
| R3 | 3 | 4.8 | 1.6 | 7.68 |
| R4 | 2 | 4.8 | 2.4 | 11.52 |
| R5 | 5 | 24 | 4.8 | 115.2 |
| R6 | 4 | 9.6 | 2.4 | 23.04 |
| R7 | 4 | 9.6 | 2.4 | 23.04 |

## 7) Kontroller

### 7.1 KVL — gerilim düşümleri toplamı

- **Ana seri kol:** V(R1) + V(R234) + V(R5) + V(R67) = 9.6 + 4.8 + 24 + 9.6 = **48 V** = kaynak gerilimi (48 V) ✔

### 7.2 KCL — düğüm akımları toplamı

- **R234 düğümü:** I(R2) + I(R3) + I(R4) = 0.8 + 1.6 + 2.4 = **4.8 mA** = gruba giren akım (4.8 mA) ✔
- **R67 düğümü:** I(R6) + I(R7) = 2.4 + 2.4 = **4.8 mA** = gruba giren akım (4.8 mA) ✔

### 7.3 Güç kontrolü

- Dirençlerin güçleri toplamı: **230.4 mW**
- Kaynağın verdiği güç: P = V · I_toplam = 48 · 4.8 = **230.4 mW**
- İkisi eşit ✔ (enerji korunumu sağlanıyor)

## 8) Simülatörde (EveryCircuit / Proto / online araç) beklenen değerler

Devreyi kurduktan sonra ölçtüğünüz değerler bu tabloyla birebir aynı çıkmalı:

| Ölçülecek | Beklenen değer |
|---|---|
| Eşdeğer direnç R_eş | 10 kΩ |
| Kaynaktan çekilen toplam akım | 4.8 mA |
| R1 → gerilim / akım | 9.6 V / 4.8 mA |
| R2 → gerilim / akım | 4.8 V / 0.8 mA |
| R3 → gerilim / akım | 4.8 V / 1.6 mA |
| R4 → gerilim / akım | 4.8 V / 2.4 mA |
| R5 → gerilim / akım | 24 V / 4.8 mA |
| R6 → gerilim / akım | 9.6 V / 2.4 mA |
| R7 → gerilim / akım | 9.6 V / 2.4 mA |

## 9) YouTube video başlığı

> **7 Dirençli Seri-Paralel DC Devre Çözümü by ______________**

*(Boşluğa kendi isminizi yazın.)*
