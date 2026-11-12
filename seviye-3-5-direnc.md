# Seviye 3 — 5 Dirençli Seri-Paralel DC Devre

## 1) Devrenin topolojisi

**R1** seri, ortada **R2 ∥ R3 ∥ R4** üçlü paralel grubu, sonda **R5** seri. Akım R1'den geçip üç kola ayrılır, birleşir, R5'ten geçer.

```
 (+)──[ R1 ]──┬──[ R2 ]──┬──[ R5 ]──(−)
              ├──[ R3 ]──┤
              └──[ R4 ]──┘
```

## 2) Verilen değerler

| Büyüklük | Değer |
|---|---|
| Kaynak gerilimi **V** | 45 V |
| R1 | 5 kΩ |
| R2 | 3 kΩ |
| R3 | 6 kΩ |
| R4 | 2 kΩ |
| R5 | 4 kΩ |

> **Birim notu:** Bütün dirençleri **kΩ**, kaynağı **V** cinsinden yazıyoruz. Volt'u kΩ'a bölünce sonuç doğrudan **mA** çıkar (çünkü V / kΩ = mA). Gerilim (V) × akım (mA) çarpımı ise **mW** verir. Böylece hiçbir yerde 1000 ile çarpma/bölme yapmaya gerek kalmaz.
>
> Sayılar 4 ondalık haneye yuvarlandı; toplamlarda son hanede çok küçük farklar görebilirsiniz, bu yuvarlamadandır.

## 3) Eşdeğer direnç — adım adım

Kural: **en içteki / en küçük paralel gruptan başla**, onu tek bir dirence indir, sonra dışa doğru ilerle. Seri olanlar en son toplanır.

**Adım 1.** **1/R234 = 1/R2 + 1/R3 + 1/R4**  (ikiden fazla paralel → ters toplam)

- 1/R234 = 1/3 + 1/6 + 1/2
- 1/R234 ≈ 0.33333 + 0.16667 + 0.5 = 1  (1/kΩ)
- R234 = 1 / 1 = **1 kΩ**

**Adım 2.** **R_eş = R1 + R234 + R5**  (seri bağlı, doğrudan toplanır)

R_eş = 5 + 1 + 4 = **10 kΩ**

➡️ **Devrenin eşdeğer direnci: R_eş = 10 kΩ**

## 4) Toplam akım (Ohm kanunu)

Kaynak, devrenin tamamını tek bir R_eş direnci gibi görür:

> I_toplam = V / R_eş = 45 V / 10 kΩ = **4.5 mA**

Volt'u kΩ'a böldüğümüz için sonuç doğrudan mA çıktı.

## 5) Her direncin gerilimi ve akımı

Hatırlatma: **seri** bağlı elemanlardan *aynı akım* geçer; **paralel** bağlı kolların *uçlarındaki gerilim aynıdır*.

- **R1** üzerinden 4.5 mA geçer → V_1 = I · R = 4.5 · 5 = **22.5 V**
- **R234** grubunun uçlarındaki gerilim: V = I · R = 4.5 · 1 = **4.5 V**
  - Bu paralel grubun her kolunda aynı **4.5 V** vardır:
    - **R2**: I = V / R = 4.5 / 3 = **1.5 mA**  (gerilimi 4.5 V)
    - **R3**: I = V / R = 4.5 / 6 = **0.75 mA**  (gerilimi 4.5 V)
    - **R4**: I = V / R = 4.5 / 2 = **2.25 mA**  (gerilimi 4.5 V)
- **R5** üzerinden 4.5 mA geçer → V_5 = I · R = 4.5 · 4 = **18 V**

## 6) Özet tablo

| Direnç | R (kΩ) | Gerilim V (V) | Akım I (mA) | Güç P = V·I (mW) |
|---|---|---|---|---|
| R1 | 5 | 22.5 | 4.5 | 101.25 |
| R2 | 3 | 4.5 | 1.5 | 6.75 |
| R3 | 6 | 4.5 | 0.75 | 3.375 |
| R4 | 2 | 4.5 | 2.25 | 10.125 |
| R5 | 4 | 18 | 4.5 | 81 |

## 7) Kontroller

### 7.1 KVL — gerilim düşümleri toplamı

- **Ana seri kol:** V(R1) + V(R234) + V(R5) = 22.5 + 4.5 + 18 = **45 V** = kaynak gerilimi (45 V) ✔

### 7.2 KCL — düğüm akımları toplamı

- **R234 düğümü:** I(R2) + I(R3) + I(R4) = 1.5 + 0.75 + 2.25 = **4.5 mA** = gruba giren akım (4.5 mA) ✔

### 7.3 Güç kontrolü

- Dirençlerin güçleri toplamı: **202.5 mW**
- Kaynağın verdiği güç: P = V · I_toplam = 45 · 4.5 = **202.5 mW**
- İkisi eşit ✔ (enerji korunumu sağlanıyor)

## 8) Simülatörde (EveryCircuit / Proto / online araç) beklenen değerler

Devreyi kurduktan sonra ölçtüğünüz değerler bu tabloyla birebir aynı çıkmalı:

| Ölçülecek | Beklenen değer |
|---|---|
| Eşdeğer direnç R_eş | 10 kΩ |
| Kaynaktan çekilen toplam akım | 4.5 mA |
| R1 → gerilim / akım | 22.5 V / 4.5 mA |
| R2 → gerilim / akım | 4.5 V / 1.5 mA |
| R3 → gerilim / akım | 4.5 V / 0.75 mA |
| R4 → gerilim / akım | 4.5 V / 2.25 mA |
| R5 → gerilim / akım | 18 V / 4.5 mA |

## 9) YouTube video başlığı

> **5 Dirençli Seri-Paralel DC Devre Çözümü by ______________**

*(Boşluğa kendi isminizi yazın.)*
