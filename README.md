# Türkçe Parola Kelime Listesi

Akılda kalır, güçlü parolalar (passphrase) üretmek için hazırlanmış **2.162 kelimelik Türkçe kelime listesi**. Liste, [rastgelesifre.com.tr](https://www.rastgelesifre.com.tr/) sitesindeki [akılda kalır parola üreticisinin](https://www.rastgelesifre.com.tr/akilda-kalir-parola-uretici) kullandığı listenin aynısıdır.

*English: a 2,162-word Turkish wordlist for generating memorable passphrases. Each randomly chosen word adds about 11.08 bits of entropy. Licensed CC BY 4.0.*

## Dosyalar

| Dosya | İçerik |
|---|---|
| `kelimeler.txt` | Her satırda bir kelime, Türkçe karakterlerle (ç, ğ, ı, ö, ş, ü) |
| `kelimeler-ascii.txt` | Aynı liste, Türkçe karakterler Latin karşılığına çevrilmiş (ç→c, ğ→g, ı→i, ö→o, ş→s, ü→u) |
| `kelimeler.json` | İki liste ve kelime sayısı, kelime başına bit değeri |

## Listenin özellikleri

- **2.162 kelime**, hepsi küçük harf, 3–9 harf uzunluğunda; günlük hayatta sık kullanılan, yazması kolay kelimeler.
- **Kendi derlememizdir**; başka bir listeden kopyalanmadı.
- Kelimelerin hiçbiri tekrar etmez. Türkçe karakterler Latin karşılığına çevrildiğinde de iki kelime aynı olmaz; bu yüzden `kelimeler-ascii.txt` kullanmak parolanın gücünü düşürmez. Türkçe karakter kabul etmeyen sitelerde veya İngilizce klavyede bu dosyayı kullanın.

## Ne kadar güçlü?

Her kelime listeden **rastgele ve birbirinden bağımsız** seçildiğinde, kelime başına güç log₂(2162) ≈ **11,08 bit**tir. Saldırganın listeyi bildiği varsayılsa bile:

| Kelime sayısı | Güç | Ortalama kırılma süresi* |
|---|---|---|
| 4 | ≈ 44,3 bit | yaklaşık 18 dakika |
| 5 | ≈ 55,4 bit | yaklaşık 27 gün |
| 6 | ≈ 66,5 bit | yaklaşık 160 yıl |
| 7 | ≈ 77,5 bit | yaklaşık 350 bin yıl |

\* Çalınmış bir şifre veritabanına karşı saniyede 10 milyar tahmin ve olasılıkların yarısı denendiğinde bulma varsayımıyla. Şifre yöneticisinin ana parolası gibi önemli parolalar için **en az 6 kelime** öneriyoruz. Hesabın ayrıntısı: [şifre entropisi nedir](https://www.rastgelesifre.com.tr/sifre-entropisi-nedir).

## Doğru kullanım

Bu güç değerleri yalnızca kelimeler **kriptografik olarak güvenli bir rastgele sayı kaynağıyla** seçildiğinde geçerlidir. Kelimeleri kendiniz seçerseniz anlamlı ve tahmin edilebilir kelimelere yönelirsiniz; parola çok daha zayıf olur.

Python ile (`secrets` modülü güvenli rastgelelik kullanır):

```python
import secrets

kelimeler = open("kelimeler.txt", encoding="utf-8").read().split()
parola = "-".join(secrets.choice(kelimeler) for _ in range(6))
print(parola)
```

Tarayıcıda kurulum gerektirmeden üretmek için: [akılda kalır parola üretici](https://www.rastgelesifre.com.tr/akilda-kalir-parola-uretici). Rastgele karakterlerden oluşan şifreler için: [rastgele şifre oluşturucu](https://www.rastgelesifre.com.tr/).

> Liste 2.162 kelime olduğu için klasik zarla seçim (Diceware, 7.776 kelime) için uygun değildir; kelimeleri bilgisayardaki güvenli rastgele sayı kaynağıyla seçin.

## Lisans

[CC BY 4.0](LICENSE). Listeyi kendi projelerinizde serbestçe kullanabilir ve değiştirebilirsiniz; kaynak olarak bu depoyu veya [rastgelesifre.com.tr](https://www.rastgelesifre.com.tr/) adresini belirtmeniz yeterlidir.
