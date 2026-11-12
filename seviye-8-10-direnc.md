# Seviye 8 — 10 Dirençli Seri-Paralel DC Devre

## 1) Devrenin topolojisi

Serbest konfigürasyon, üç paralel bölge. Sırayla: **R1** seri → **R2 ∥ R3** → ikinci paralel grup (**R4+R5 seri kolu** ile **R6+R7 seri kolu** paralel) → **R8** seri → **R9 ∥ R10**.

```
 (+)──[ R1 ]──┬──[ R2 ]──┬──┬──[ R4 ]──[ R5 ]──┬──[ R8 ]──┬──[ R9 ]───┬──(−)
              │          │  │                  │          │           │
              └──[ R3 ]──┘  └──[ R6 ]──[ R7 ]──┘          └──[ R10 ]──┘
```

## 2) Verilen değerler

| Büyüklük | Değer |
|---|---|
| Kaynak gerilimi **V** | 56 V |
| R1 | 2 kΩ |
| R2 | 10 kΩ |
| R3 | 10 kΩ |
| R4 | 3 kΩ |
| R5 | 4 kΩ |
| R6 | 1 kΩ |
| R7 | 6 kΩ |
| R8 | 1 kΩ |
| R9 | 5 kΩ |
| R10 | 5 kΩ |

> **Birim notu:** Bütün dirençleri **kΩ**, kaynağı **V** cinsinden yazıyoruz. Volt'u kΩ'a bölünce sonuç doğrudan **mA** çıkar (çünkü V / kΩ = mA). Gerilim (V) × akım (mA) çarpımı ise **mW** verir. Böylece hiçbir yerde 1000 ile çarpma/bölme yapmaya gerek kalmaz.
>
> Sayılar 4 ondalık haneye yuvarlandı; toplamlarda son hanede çok küçük farklar görebilirsiniz, bu yuvarlamadandır.

## 3) Eşdeğer direnç — adım adım

Kural: **en içteki / en küçük paralel gruptan başla**, onu tek bir dirence indir, sonra dışa doğru ilerle. Seri olanlar en son toplanır.

**Adım 1.** **R23 = (R2 · R3) / (R2 + R3)**  (iki direnç paralel → çarpım/toplam)

- Çarpım: 10 · 10 = 100
- Toplam: 10 + 10 = 20
- R23 = 100 / 20 = **5 kΩ**

**Adım 2.** **R45 = R4 + R5**  (seri bağlı, doğrudan toplanır)

R45 = 3 + 4 = **7 kΩ**

**Adım 3.** **R67 = R6 + R7**  (seri bağlı, doğrudan toplanır)

R67 = 1 + 6 = **7 kΩ**

**Adım 4.** **RA = (R45 · R67) / (R45 + R67)**  (iki direnç paralel → çarpım/toplam)

- Çarpım: 7 · 7 = 49
- Toplam: 7 + 7 = 14
- RA = 49 / 14 = **3.5 kΩ**

**Adım 5.** **R910 = (R9 · R10) / (R9 + R10)**  (iki direnç paralel → çarpım/toplam)

- Çarpım: 5 · 5 = 25
- Toplam: 5 + 5 = 10
- R910 = 25 / 10 = **2.5 kΩ**

**Adım 6.** **R_eş = R1 + R23 + RA + R8 + R910**  (seri bağlı, doğrudan toplanır)

R_eş = 2 + 5 + 3.5 + 1 + 2.5 = **14 kΩ**

➡️ **Devrenin eşdeğer direnci: R_eş = 14 kΩ**

## 4) Toplam akım (Ohm kanunu)

Kaynak, devrenin tamamını tek bir R_eş direnci gibi görür:

> I_toplam = V / R_eş = 56 V / 14 kΩ = **4 mA**

Volt'u kΩ'a böldüğümüz için sonuç doğrudan mA çıktı.

## 5) Her direncin gerilimi ve akımı

Hatırlatma: **seri** bağlı elemanlardan *aynı akım* geçer; **paralel** bağlı kolların *uçlarındaki gerilim aynıdır*.

- **R1** üzerinden 4 mA geçer → V_1 = I · R = 4 · 2 = **8 V**
- **R23** grubunun uçlarındaki gerilim: V = I · R = 4 · 5 = **20 V**
  - Bu paralel grubun her kolunda aynı **20 V** vardır:
    - **R2**: I = V / R = 20 / 10 = **2 mA**  (gerilimi 20 V)
    - **R3**: I = V / R = 20 / 10 = **2 mA**  (gerilimi 20 V)
- **RA** grubunun uçlarındaki gerilim: V = I · R = 4 · 3.5 = **14 V**
  - Bu paralel grubun her kolunda aynı **14 V** vardır:
    - **R45** kolu: I = V / R = 14 / 7 = **2 mA**
      - **R4** üzerinden 2 mA geçer → V_4 = I · R = 2 · 3 = **6 V**
      - **R5** üzerinden 2 mA geçer → V_5 = I · R = 2 · 4 = **8 V**
    - **R67** kolu: I = V / R = 14 / 7 = **2 mA**
      - **R6** üzerinden 2 mA geçer → V_6 = I · R = 2 · 1 = **2 V**
      - **R7** üzerinden 2 mA geçer → V_7 = I · R = 2 · 6 = **12 V**
- **R8** üzerinden 4 mA geçer → V_8 = I · R = 4 · 1 = **4 V**
- **R910** grubunun uçlarındaki gerilim: V = I · R = 4 · 2.5 = **10 V**
  - Bu paralel grubun her kolunda aynı **10 V** vardır:
    - **R9**: I = V / R = 10 / 5 = **2 mA**  (gerilimi 10 V)
    - **R10**: I = V / R = 10 / 5 = **2 mA**  (gerilimi 10 V)

## 6) Özet tablo

| Direnç | R (kΩ) | Gerilim V (V) | Akım I (mA) | Güç P = V·I (mW) |
|---|---|---|---|---|
| R1 | 2 | 8 | 4 | 32 |
| R2 | 10 | 20 | 2 | 40 |
| R3 | 10 | 20 | 2 | 40 |
| R4 | 3 | 6 | 2 | 12 |
| R5 | 4 | 8 | 2 | 16 |
| R6 | 1 | 2 | 2 | 4 |
| R7 | 6 | 12 | 2 | 24 |
| R8 | 1 | 4 | 4 | 16 |
| R9 | 5 | 10 | 2 | 20 |
| R10 | 5 | 10 | 2 | 20 |

## 7) Kontroller

### 7.1 KVL — gerilim düşümleri toplamı

- **Ana seri kol:** V(R1) + V(R23) + V(RA) + V(R8) + V(R910) = 8 + 20 + 14 + 4 + 10 = **56 V** = kaynak gerilimi (56 V) ✔
- **R45 kolu (seri):** V(R4) + V(R5) = 6 + 8 = **14 V** = bu kolun uçlarındaki gerilim (14 V) ✔
- **R67 kolu (seri):** V(R6) + V(R7) = 2 + 12 = **14 V** = bu kolun uçlarındaki gerilim (14 V) ✔

### 7.2 KCL — düğüm akımları toplamı

- **R23 düğümü:** I(R2) + I(R3) = 2 + 2 = **4 mA** = gruba giren akım (4 mA) ✔
- **RA düğümü:** I(R45) + I(R67) = 2 + 2 = **4 mA** = gruba giren akım (4 mA) ✔
- **R910 düğümü:** I(R9) + I(R10) = 2 + 2 = **4 mA** = gruba giren akım (4 mA) ✔

### 7.3 Güç kontrolü

- Dirençlerin güçleri toplamı: **224 mW**
- Kaynağın verdiği güç: P = V · I_toplam = 56 · 4 = **224 mW**
- İkisi eşit ✔ (enerji korunumu sağlanıyor)

## 8) Simülatörde (EveryCircuit / Proto / online araç) beklenen değerler

Devreyi kurduktan sonra ölçtüğünüz değerler bu tabloyla birebir aynı çıkmalı:

| Ölçülecek | Beklenen değer |
|---|---|
| Eşdeğer direnç R_eş | 14 kΩ |
| Kaynaktan çekilen toplam akım | 4 mA |
| R1 → gerilim / akım | 8 V / 4 mA |
| R2 → gerilim / akım | 20 V / 2 mA |
| R3 → gerilim / akım | 20 V / 2 mA |
| R4 → gerilim / akım | 6 V / 2 mA |
| R5 → gerilim / akım | 8 V / 2 mA |
| R6 → gerilim / akım | 2 V / 2 mA |
| R7 → gerilim / akım | 12 V / 2 mA |
| R8 → gerilim / akım | 4 V / 4 mA |
| R9 → gerilim / akım | 10 V / 2 mA |
| R10 → gerilim / akım | 10 V / 2 mA |

## 9) YouTube video başlığı

> **10 Dirençli Seri-Paralel DC Devre Çözümü by ______________**

*(Boşluğa kendi isminizi yazın.)*
