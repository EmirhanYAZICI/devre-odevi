# Seviye 6 — 8 Dirençli Seri-Paralel DC Devre

## 1) Devrenin topolojisi

Serbest konfigürasyon. Sırayla: **R1** seri → birinci paralel grup (**R2+R3 seri kolu** ile **R4** paralel) → **R5** seri → ikinci paralel grup (**R6** ile **R7+R8 seri kolu** paralel). Burada paralel kolların *içinde* seri dirençler var; önce o kolların kendi toplamı bulunur, sonra paralel hesabı yapılır.

```
 (+)──[ R1 ]──┬──[ R2 ]──[ R3 ]──┬──[ R5 ]──┬──[ R6 ]───────────┬──(−)
              │                  │          │                   │
              └───────[ R4 ]─────┘          └──[ R7 ]──[ R8 ]───┘
```

## 2) Verilen değerler

| Büyüklük | Değer |
|---|---|
| Kaynak gerilimi **V** | 52 V |
| R1 | 4 kΩ |
| R2 | 3 kΩ |
| R3 | 5 kΩ |
| R4 | 8 kΩ |
| R5 | 2 kΩ |
| R6 | 6 kΩ |
| R7 | 1 kΩ |
| R8 | 5 kΩ |

> **Birim notu:** Bütün dirençleri **kΩ**, kaynağı **V** cinsinden yazıyoruz. Volt'u kΩ'a bölünce sonuç doğrudan **mA** çıkar (çünkü V / kΩ = mA). Gerilim (V) × akım (mA) çarpımı ise **mW** verir. Böylece hiçbir yerde 1000 ile çarpma/bölme yapmaya gerek kalmaz.
>
> Sayılar 4 ondalık haneye yuvarlandı; toplamlarda son hanede çok küçük farklar görebilirsiniz, bu yuvarlamadandır.

## 3) Eşdeğer direnç — adım adım

Kural: **en içteki / en küçük paralel gruptan başla**, onu tek bir dirence indir, sonra dışa doğru ilerle. Seri olanlar en son toplanır.

**Adım 1.** **R23 = R2 + R3**  (seri bağlı, doğrudan toplanır)

R23 = 3 + 5 = **8 kΩ**

**Adım 2.** **RA = (R23 · R4) / (R23 + R4)**  (iki direnç paralel → çarpım/toplam)

- Çarpım: 8 · 8 = 64
- Toplam: 8 + 8 = 16
- RA = 64 / 16 = **4 kΩ**

**Adım 3.** **R78 = R7 + R8**  (seri bağlı, doğrudan toplanır)

R78 = 1 + 5 = **6 kΩ**

**Adım 4.** **RB = (R6 · R78) / (R6 + R78)**  (iki direnç paralel → çarpım/toplam)

- Çarpım: 6 · 6 = 36
- Toplam: 6 + 6 = 12
- RB = 36 / 12 = **3 kΩ**

**Adım 5.** **R_eş = R1 + RA + R5 + RB**  (seri bağlı, doğrudan toplanır)

R_eş = 4 + 4 + 2 + 3 = **13 kΩ**

➡️ **Devrenin eşdeğer direnci: R_eş = 13 kΩ**

## 4) Toplam akım (Ohm kanunu)

Kaynak, devrenin tamamını tek bir R_eş direnci gibi görür:

> I_toplam = V / R_eş = 52 V / 13 kΩ = **4 mA**

Volt'u kΩ'a böldüğümüz için sonuç doğrudan mA çıktı.

## 5) Her direncin gerilimi ve akımı

Hatırlatma: **seri** bağlı elemanlardan *aynı akım* geçer; **paralel** bağlı kolların *uçlarındaki gerilim aynıdır*.

- **R1** üzerinden 4 mA geçer → V_1 = I · R = 4 · 4 = **16 V**
- **RA** grubunun uçlarındaki gerilim: V = I · R = 4 · 4 = **16 V**
  - Bu paralel grubun her kolunda aynı **16 V** vardır:
    - **R23** kolu: I = V / R = 16 / 8 = **2 mA**
      - **R2** üzerinden 2 mA geçer → V_2 = I · R = 2 · 3 = **6 V**
      - **R3** üzerinden 2 mA geçer → V_3 = I · R = 2 · 5 = **10 V**
    - **R4**: I = V / R = 16 / 8 = **2 mA**  (gerilimi 16 V)
- **R5** üzerinden 4 mA geçer → V_5 = I · R = 4 · 2 = **8 V**
- **RB** grubunun uçlarındaki gerilim: V = I · R = 4 · 3 = **12 V**
  - Bu paralel grubun her kolunda aynı **12 V** vardır:
    - **R6**: I = V / R = 12 / 6 = **2 mA**  (gerilimi 12 V)
    - **R78** kolu: I = V / R = 12 / 6 = **2 mA**
      - **R7** üzerinden 2 mA geçer → V_7 = I · R = 2 · 1 = **2 V**
      - **R8** üzerinden 2 mA geçer → V_8 = I · R = 2 · 5 = **10 V**

## 6) Özet tablo

| Direnç | R (kΩ) | Gerilim V (V) | Akım I (mA) | Güç P = V·I (mW) |
|---|---|---|---|---|
| R1 | 4 | 16 | 4 | 64 |
| R2 | 3 | 6 | 2 | 12 |
| R3 | 5 | 10 | 2 | 20 |
| R4 | 8 | 16 | 2 | 32 |
| R5 | 2 | 8 | 4 | 32 |
| R6 | 6 | 12 | 2 | 24 |
| R7 | 1 | 2 | 2 | 4 |
| R8 | 5 | 10 | 2 | 20 |

## 7) Kontroller

### 7.1 KVL — gerilim düşümleri toplamı

- **Ana seri kol:** V(R1) + V(RA) + V(R5) + V(RB) = 16 + 16 + 8 + 12 = **52 V** = kaynak gerilimi (52 V) ✔
- **R23 kolu (seri):** V(R2) + V(R3) = 6 + 10 = **16 V** = bu kolun uçlarındaki gerilim (16 V) ✔
- **R78 kolu (seri):** V(R7) + V(R8) = 2 + 10 = **12 V** = bu kolun uçlarındaki gerilim (12 V) ✔

### 7.2 KCL — düğüm akımları toplamı

- **RA düğümü:** I(R23) + I(R4) = 2 + 2 = **4 mA** = gruba giren akım (4 mA) ✔
- **RB düğümü:** I(R6) + I(R78) = 2 + 2 = **4 mA** = gruba giren akım (4 mA) ✔

### 7.3 Güç kontrolü

- Dirençlerin güçleri toplamı: **208 mW**
- Kaynağın verdiği güç: P = V · I_toplam = 52 · 4 = **208 mW**
- İkisi eşit ✔ (enerji korunumu sağlanıyor)

## 8) Simülatörde (EveryCircuit / Proto / online araç) beklenen değerler

Devreyi kurduktan sonra ölçtüğünüz değerler bu tabloyla birebir aynı çıkmalı:

| Ölçülecek | Beklenen değer |
|---|---|
| Eşdeğer direnç R_eş | 13 kΩ |
| Kaynaktan çekilen toplam akım | 4 mA |
| R1 → gerilim / akım | 16 V / 4 mA |
| R2 → gerilim / akım | 6 V / 2 mA |
| R3 → gerilim / akım | 10 V / 2 mA |
| R4 → gerilim / akım | 16 V / 2 mA |
| R5 → gerilim / akım | 8 V / 4 mA |
| R6 → gerilim / akım | 12 V / 2 mA |
| R7 → gerilim / akım | 2 V / 2 mA |
| R8 → gerilim / akım | 10 V / 2 mA |

## 9) YouTube video başlığı

> **8 Dirençli Seri-Paralel DC Devre Çözümü by ______________**

*(Boşluğa kendi isminizi yazın.)*
