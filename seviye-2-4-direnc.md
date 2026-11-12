# Seviye 2 — 4 Dirençli Seri-Paralel DC Devre

## 1) Devrenin topolojisi

**R1** seri, sonra **R2 ∥ R3** paralel ikilisi, en sonda yine seri olarak **R4** vardır. Akım R1'den geçer, paralel grupta ikiye ayrılır, birleşir ve R4'ten geçerek kaynağa döner.

```
 (+)──[ R1 ]──┬──[ R2 ]──┬──[ R4 ]──(−)
              │          │
              └──[ R3 ]──┘
```

## 2) Verilen değerler

| Büyüklük | Değer |
|---|---|
| Kaynak gerilimi **V** | 36 V |
| R1 | 2 kΩ |
| R2 | 4 kΩ |
| R3 | 4 kΩ |
| R4 | 5 kΩ |

> **Birim notu:** Bütün dirençleri **kΩ**, kaynağı **V** cinsinden yazıyoruz. Volt'u kΩ'a bölünce sonuç doğrudan **mA** çıkar (çünkü V / kΩ = mA). Gerilim (V) × akım (mA) çarpımı ise **mW** verir. Böylece hiçbir yerde 1000 ile çarpma/bölme yapmaya gerek kalmaz.
>
> Sayılar 4 ondalık haneye yuvarlandı; toplamlarda son hanede çok küçük farklar görebilirsiniz, bu yuvarlamadandır.

## 3) Eşdeğer direnç — adım adım

Kural: **en içteki / en küçük paralel gruptan başla**, onu tek bir dirence indir, sonra dışa doğru ilerle. Seri olanlar en son toplanır.

**Adım 1.** **R23 = (R2 · R3) / (R2 + R3)**  (iki direnç paralel → çarpım/toplam)

- Çarpım: 4 · 4 = 16
- Toplam: 4 + 4 = 8
- R23 = 16 / 8 = **2 kΩ**

**Adım 2.** **R_eş = R1 + R23 + R4**  (seri bağlı, doğrudan toplanır)

R_eş = 2 + 2 + 5 = **9 kΩ**

➡️ **Devrenin eşdeğer direnci: R_eş = 9 kΩ**

## 4) Toplam akım (Ohm kanunu)

Kaynak, devrenin tamamını tek bir R_eş direnci gibi görür:

> I_toplam = V / R_eş = 36 V / 9 kΩ = **4 mA**

Volt'u kΩ'a böldüğümüz için sonuç doğrudan mA çıktı.

## 5) Her direncin gerilimi ve akımı

Hatırlatma: **seri** bağlı elemanlardan *aynı akım* geçer; **paralel** bağlı kolların *uçlarındaki gerilim aynıdır*.

- **R1** üzerinden 4 mA geçer → V_1 = I · R = 4 · 2 = **8 V**
- **R23** grubunun uçlarındaki gerilim: V = I · R = 4 · 2 = **8 V**
  - Bu paralel grubun her kolunda aynı **8 V** vardır:
    - **R2**: I = V / R = 8 / 4 = **2 mA**  (gerilimi 8 V)
    - **R3**: I = V / R = 8 / 4 = **2 mA**  (gerilimi 8 V)
- **R4** üzerinden 4 mA geçer → V_4 = I · R = 4 · 5 = **20 V**

## 6) Özet tablo

| Direnç | R (kΩ) | Gerilim V (V) | Akım I (mA) | Güç P = V·I (mW) |
|---|---|---|---|---|
| R1 | 2 | 8 | 4 | 32 |
| R2 | 4 | 8 | 2 | 16 |
| R3 | 4 | 8 | 2 | 16 |
| R4 | 5 | 20 | 4 | 80 |

## 7) Kontroller

### 7.1 KVL — gerilim düşümleri toplamı

- **Ana seri kol:** V(R1) + V(R23) + V(R4) = 8 + 8 + 20 = **36 V** = kaynak gerilimi (36 V) ✔

### 7.2 KCL — düğüm akımları toplamı

- **R23 düğümü:** I(R2) + I(R3) = 2 + 2 = **4 mA** = gruba giren akım (4 mA) ✔

### 7.3 Güç kontrolü

- Dirençlerin güçleri toplamı: **144 mW**
- Kaynağın verdiği güç: P = V · I_toplam = 36 · 4 = **144 mW**
- İkisi eşit ✔ (enerji korunumu sağlanıyor)

## 8) Simülatörde (EveryCircuit / Proto / online araç) beklenen değerler

Devreyi kurduktan sonra ölçtüğünüz değerler bu tabloyla birebir aynı çıkmalı:

| Ölçülecek | Beklenen değer |
|---|---|
| Eşdeğer direnç R_eş | 9 kΩ |
| Kaynaktan çekilen toplam akım | 4 mA |
| R1 → gerilim / akım | 8 V / 4 mA |
| R2 → gerilim / akım | 8 V / 2 mA |
| R3 → gerilim / akım | 8 V / 2 mA |
| R4 → gerilim / akım | 20 V / 4 mA |

## 9) YouTube video başlığı

> **4 Dirençli Seri-Paralel DC Devre Çözümü by ______________**

*(Boşluğa kendi isminizi yazın.)*
