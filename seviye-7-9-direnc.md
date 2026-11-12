# Seviye 7 — 9 Dirençli Seri-Paralel DC Devre

## 1) Devrenin topolojisi

Serbest konfigürasyon, **iç içe (nested)** yapı. Sırayla: **R1** seri → bir paralel grup; bu grubun üst kolu **R2 ile (R3 ∥ R4)**'ün serisi, alt kolu tek başına **R5** → **R6** seri → **R7 ∥ R8 ∥ R9** üçlü paralel. En içteki R3 ∥ R4 ikilisinden başlanır.

```
 (+)──[ R1 ]──┬──[ R2 ]──┬──[ R3 ]──┬──┬──[ R6 ]──┬──[ R7 ]──┬──(−)
              │          └──[ R4 ]──┘  │          ├──[ R8 ]──┤
              └────────[ R5 ]──────────┘          └──[ R9 ]──┘
```

## 2) Verilen değerler

| Büyüklük | Değer |
|---|---|
| Kaynak gerilimi **V** | 60 V |
| R1 | 3 kΩ |
| R2 | 5 kΩ |
| R3 | 4 kΩ |
| R4 | 4 kΩ |
| R5 | 7 kΩ |
| R6 | 6 kΩ |
| R7 | 10 kΩ |
| R8 | 10 kΩ |
| R9 | 5 kΩ |

> **Birim notu:** Bütün dirençleri **kΩ**, kaynağı **V** cinsinden yazıyoruz. Volt'u kΩ'a bölünce sonuç doğrudan **mA** çıkar (çünkü V / kΩ = mA). Gerilim (V) × akım (mA) çarpımı ise **mW** verir. Böylece hiçbir yerde 1000 ile çarpma/bölme yapmaya gerek kalmaz.
>
> Sayılar 4 ondalık haneye yuvarlandı; toplamlarda son hanede çok küçük farklar görebilirsiniz, bu yuvarlamadandır.

## 3) Eşdeğer direnç — adım adım

Kural: **en içteki / en küçük paralel gruptan başla**, onu tek bir dirence indir, sonra dışa doğru ilerle. Seri olanlar en son toplanır.

**Adım 1.** **R34 = (R3 · R4) / (R3 + R4)**  (iki direnç paralel → çarpım/toplam)

- Çarpım: 4 · 4 = 16
- Toplam: 4 + 4 = 8
- R34 = 16 / 8 = **2 kΩ**

**Adım 2.** **RA = R2 + R34**  (seri bağlı, doğrudan toplanır)

RA = 5 + 2 = **7 kΩ**

**Adım 3.** **RB = (RA · R5) / (RA + R5)**  (iki direnç paralel → çarpım/toplam)

- Çarpım: 7 · 7 = 49
- Toplam: 7 + 7 = 14
- RB = 49 / 14 = **3.5 kΩ**

**Adım 4.** **1/R789 = 1/R7 + 1/R8 + 1/R9**  (ikiden fazla paralel → ters toplam)

- 1/R789 = 1/10 + 1/10 + 1/5
- 1/R789 ≈ 0.1 + 0.1 + 0.2 = 0.4  (1/kΩ)
- R789 = 1 / 0.4 = **2.5 kΩ**

**Adım 5.** **R_eş = R1 + RB + R6 + R789**  (seri bağlı, doğrudan toplanır)

R_eş = 3 + 3.5 + 6 + 2.5 = **15 kΩ**

➡️ **Devrenin eşdeğer direnci: R_eş = 15 kΩ**

## 4) Toplam akım (Ohm kanunu)

Kaynak, devrenin tamamını tek bir R_eş direnci gibi görür:

> I_toplam = V / R_eş = 60 V / 15 kΩ = **4 mA**

Volt'u kΩ'a böldüğümüz için sonuç doğrudan mA çıktı.

## 5) Her direncin gerilimi ve akımı

Hatırlatma: **seri** bağlı elemanlardan *aynı akım* geçer; **paralel** bağlı kolların *uçlarındaki gerilim aynıdır*.

- **R1** üzerinden 4 mA geçer → V_1 = I · R = 4 · 3 = **12 V**
- **RB** grubunun uçlarındaki gerilim: V = I · R = 4 · 3.5 = **14 V**
  - Bu paralel grubun her kolunda aynı **14 V** vardır:
    - **RA** kolu: I = V / R = 14 / 7 = **2 mA**
      - **R2** üzerinden 2 mA geçer → V_2 = I · R = 2 · 5 = **10 V**
      - **R34** grubunun uçlarındaki gerilim: V = I · R = 2 · 2 = **4 V**
        - Bu paralel grubun her kolunda aynı **4 V** vardır:
          - **R3**: I = V / R = 4 / 4 = **1 mA**  (gerilimi 4 V)
          - **R4**: I = V / R = 4 / 4 = **1 mA**  (gerilimi 4 V)
    - **R5**: I = V / R = 14 / 7 = **2 mA**  (gerilimi 14 V)
- **R6** üzerinden 4 mA geçer → V_6 = I · R = 4 · 6 = **24 V**
- **R789** grubunun uçlarındaki gerilim: V = I · R = 4 · 2.5 = **10 V**
  - Bu paralel grubun her kolunda aynı **10 V** vardır:
    - **R7**: I = V / R = 10 / 10 = **1 mA**  (gerilimi 10 V)
    - **R8**: I = V / R = 10 / 10 = **1 mA**  (gerilimi 10 V)
    - **R9**: I = V / R = 10 / 5 = **2 mA**  (gerilimi 10 V)

## 6) Özet tablo

| Direnç | R (kΩ) | Gerilim V (V) | Akım I (mA) | Güç P = V·I (mW) |
|---|---|---|---|---|
| R1 | 3 | 12 | 4 | 48 |
| R2 | 5 | 10 | 2 | 20 |
| R3 | 4 | 4 | 1 | 4 |
| R4 | 4 | 4 | 1 | 4 |
| R5 | 7 | 14 | 2 | 28 |
| R6 | 6 | 24 | 4 | 96 |
| R7 | 10 | 10 | 1 | 10 |
| R8 | 10 | 10 | 1 | 10 |
| R9 | 5 | 10 | 2 | 20 |

## 7) Kontroller

### 7.1 KVL — gerilim düşümleri toplamı

- **Ana seri kol:** V(R1) + V(RB) + V(R6) + V(R789) = 12 + 14 + 24 + 10 = **60 V** = kaynak gerilimi (60 V) ✔
- **RA kolu (seri):** V(R2) + V(R34) = 10 + 4 = **14 V** = bu kolun uçlarındaki gerilim (14 V) ✔

### 7.2 KCL — düğüm akımları toplamı

- **RB düğümü:** I(RA) + I(R5) = 2 + 2 = **4 mA** = gruba giren akım (4 mA) ✔
- **R34 düğümü:** I(R3) + I(R4) = 1 + 1 = **2 mA** = gruba giren akım (2 mA) ✔
- **R789 düğümü:** I(R7) + I(R8) + I(R9) = 1 + 1 + 2 = **4 mA** = gruba giren akım (4 mA) ✔

### 7.3 Güç kontrolü

- Dirençlerin güçleri toplamı: **240 mW**
- Kaynağın verdiği güç: P = V · I_toplam = 60 · 4 = **240 mW**
- İkisi eşit ✔ (enerji korunumu sağlanıyor)

## 8) Simülatörde (EveryCircuit / Proto / online araç) beklenen değerler

Devreyi kurduktan sonra ölçtüğünüz değerler bu tabloyla birebir aynı çıkmalı:

| Ölçülecek | Beklenen değer |
|---|---|
| Eşdeğer direnç R_eş | 15 kΩ |
| Kaynaktan çekilen toplam akım | 4 mA |
| R1 → gerilim / akım | 12 V / 4 mA |
| R2 → gerilim / akım | 10 V / 2 mA |
| R3 → gerilim / akım | 4 V / 1 mA |
| R4 → gerilim / akım | 4 V / 1 mA |
| R5 → gerilim / akım | 14 V / 2 mA |
| R6 → gerilim / akım | 24 V / 4 mA |
| R7 → gerilim / akım | 10 V / 1 mA |
| R8 → gerilim / akım | 10 V / 1 mA |
| R9 → gerilim / akım | 10 V / 2 mA |

## 9) YouTube video başlığı

> **9 Dirençli Seri-Paralel DC Devre Çözümü by ______________**

*(Boşluğa kendi isminizi yazın.)*
