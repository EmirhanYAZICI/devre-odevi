# Elektrik Ödevi — Seri-Paralel DC Devre Çözümleri

Her seviye ayrı bir dosyada, hiçbir ara işlem atlanmadan çözülmüştür. Her seviye 2 puan.

| Seviye | Direnç sayısı | Kaynak (V) | R_eş (kΩ) | I_toplam (mA) | Dosya |
|---|---|---|---|---|---|
| 1 | 3 | 26 | 5.2 | 5 | [seviye-1-3-direnc.md](seviye-1-3-direnc.md) |
| 2 | 4 | 36 | 9 | 4 | [seviye-2-4-direnc.md](seviye-2-4-direnc.md) |
| 3 | 5 | 45 | 10 | 4.5 | [seviye-3-5-direnc.md](seviye-3-5-direnc.md) |
| 4 | 6 | 30 | 10 | 3 | [seviye-4-6-direnc.md](seviye-4-6-direnc.md) |
| 5 | 7 | 48 | 10 | 4.8 | [seviye-5-7-direnc.md](seviye-5-7-direnc.md) |
| 6 | 8 | 52 | 13 | 4 | [seviye-6-8-direnc.md](seviye-6-8-direnc.md) |
| 7 | 9 | 60 | 15 | 4 | [seviye-7-9-direnc.md](seviye-7-9-direnc.md) |
| 8 | 10 | 56 | 14 | 4 | [seviye-8-10-direnc.md](seviye-8-10-direnc.md) |

## Her dosyada ne var?
1. Devrenin topolojisi (hangi direnç seri, hangileri paralel) + ASCII şema
2. Verilen değerler tablosu
3. Eşdeğer direnç hesabı, adım adım (önce paralel gruplar, sonra seri toplama)
4. Ohm kanunu ile toplam akım
5. Her direncin üzerindeki gerilim ve akım
6. Özet tablo (R, V, I, P)
7. KVL / KCL / güç kontrolleri
8. Simülatörde doğrulama tablosu
9. YouTube başlığı önerisi

## Birim kuralı (bütün dosyalarda geçerli)
Dirençler **kΩ**, gerilimler **V**. Buna göre V / kΩ = **mA**, V × mA = **mW**.
Bu yüzden hiçbir yerde 1000'e bölme/çarpma yapılmadı.

## Videoyu çekerken önerilen sıra
1. Şemayı kâğıda çiz, hangi grubun paralel olduğunu göster.
2. Verilen değerleri oku.
3. Eşdeğer direnci adım adım hesapla (en içteki paralelden başla).
4. I_toplam = V / R_eş.
5. Geri dönüp her direncin V ve I değerini bul.
6. KVL, KCL ve güç kontrolünü yaparak doğruluğu göster.
7. Aynı devreyi simülatörde kur, 8. bölümdeki tabloyla karşılaştır.
