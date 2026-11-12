# Seviye 1 — 3 Dirençli Seri-Paralel DC Devre

## 1) Devrenin topolojisi

**R1** kaynağa seri bağlıdır; ardından **R2** ile **R3** birbirine paralel bağlanmıştır. Yani akım önce R1'den tek parça geçer, sonra ikiye ayrılıp R2 ve R3 kollarından akar ve tekrar birleşir.

```
 (+)──[ R1 ]──┬──[ R2 ]──┬──(−)
              │          │
              └──[ R3 ]──┘
```

## 2) Verilen değerler

| Büyüklük | Değer |
|---|---|
| Kaynak gerilimi **V** | 26 V |
| R1 | 4 kΩ |
| R2 | 2 kΩ |
| R3 | 3 kΩ |

> **Birim notu:** Bütün dirençleri **kΩ**, kaynağı **V** cinsinden yazıyoruz. Volt'u kΩ'a bölünce sonuç doğrudan **mA** çıkar (çünkü V / kΩ = mA). Gerilim (V) × akım (mA) çarpımı ise **mW** verir. Böylece hiçbir yerde 1000 ile çarpma/bölme yapmaya gerek kalmaz.
>
> Sayılar 4 ondalık haneye yuvarlandı; toplamlarda son hanede çok küçük farklar görebilirsiniz, bu yuvarlamadandır.

## 3) Eşdeğer direnç — adım adım

Kural: **en içteki / en küçük paralel gruptan başla**, onu tek bir dirence indir, sonra dışa doğru ilerle. Seri olanlar en son toplanır.

**Adım 1.** **R23 = (R2 · R3) / (R2 + R3)**  (iki direnç paralel → çarpım/toplam)

- Çarpım: 2 · 3 = 6
- Toplam: 2 + 3 = 5
- R23 = 6 / 5 = **1.2 kΩ**

**Adım 2.** **R_eş = R1 + R23**  (seri bağlı, doğrudan toplanır)

R_eş = 4 + 1.2 = **5.2 kΩ**

➡️ **Devrenin eşdeğer direnci: R_eş = 5.2 kΩ**

## 4) Toplam akım (Ohm kanunu)

Kaynak, devrenin tamamını tek bir R_eş direnci gibi görür:

> I_toplam = V / R_eş = 26 V / 5.2 kΩ = **5 mA**

Volt'u kΩ'a böldüğümüz için sonuç doğrudan mA çıktı.

## 5) Her direncin gerilimi ve akımı

Hatırlatma: **seri** bağlı elemanlardan *aynı akım* geçer; **paralel** bağlı kolların *uçlarındaki gerilim aynıdır*.

- **R1** üzerinden 5 mA geçer → V_1 = I · R = 5 · 4 = **20 V**
- **R23** grubunun uçlarındaki gerilim: V = I · R = 5 · 1.2 = **6 V**
  - Bu paralel grubun her kolunda aynı **6 V** vardır:
    - **R2**: I = V / R = 6 / 2 = **3 mA**  (gerilimi 6 V)
    - **R3**: I = V / R = 6 / 3 = **2 mA**  (gerilimi 6 V)

## 6) Özet tablo

| Direnç | R (kΩ) | Gerilim V (V) | Akım I (mA) | Güç P = V·I (mW) |
|---|---|---|---|---|
| R1 | 4 | 20 | 5 | 100 |
| R2 | 2 | 6 | 3 | 18 |
| R3 | 3 | 6 | 2 | 12 |

## 7) Kontroller

### 7.1 KVL — gerilim düşümleri toplamı

- **Ana seri kol:** V(R1) + V(R23) = 20 + 6 = **26 V** = kaynak gerilimi (26 V) ✔

### 7.2 KCL — düğüm akımları toplamı

- **R23 düğümü:** I(R2) + I(R3) = 3 + 2 = **5 mA** = gruba giren akım (5 mA) ✔

### 7.3 Güç kontrolü

- Dirençlerin güçleri toplamı: **130 mW**
- Kaynağın verdiği güç: P = V · I_toplam = 26 · 5 = **130 mW**
- İkisi eşit ✔ (enerji korunumu sağlanıyor)

## 8) Simülatörde (EveryCircuit / Proto / online araç) beklenen değerler

Devreyi kurduktan sonra ölçtüğünüz değerler bu tabloyla birebir aynı çıkmalı:

| Ölçülecek | Beklenen değer |
|---|---|
| Eşdeğer direnç R_eş | 5.2 kΩ |
| Kaynaktan çekilen toplam akım | 5 mA |
| R1 → gerilim / akım | 20 V / 5 mA |
| R2 → gerilim / akım | 6 V / 3 mA |
| R3 → gerilim / akım | 6 V / 2 mA |

## 9) YouTube video başlığı

> **3 Dirençli Seri-Paralel DC Devre Çözümü by ______________**

*(Boşluğa kendi isminizi yazın.)*
