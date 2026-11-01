# AGS Soru Bankası: yapılandırma

Bu depo yalnızca **herkese açık** tek bir küçük dosya içerir: `exam-dates.json` (resmî AGS sınav tarihleri).
Soru bankası ve uygulama kodu bu depoda değildir.

Uygulama bu dosyayı açılışta ve günde birkaç kez indirir; değiştirdiğin tarih **uygulama güncellemesi olmadan** herkeste görünür.

## Yeni tarih eklemek

ÖSYM sınav tarihini duyurunca `exam-dates.json` içindeki `exams` listesine yeni bir kayıt ekle ve `main` dalına gönder:

```json
{ "id": "ags-2027", "name": "2027 MEB-AGS", "date": "2027-07-25", "time": "10:15", "durationMin": 110 }
```

- `id`: benzersiz, en çok 40 karakter.
- `name`: ekranda görünen ad (en çok 80 karakter).
- `date`: `YYYY-AA-GG` (var olan bir gün olmalı).
- `time` (isteğe bağlı): `SS:DD`, 24 saat.
- `durationMin` (isteğe bağlı): 1–600.
- `schema` her zaman `1` kalır; en fazla 24 kayıt.
- Geçmiş tarihleri silmek zorunda değilsin; uygulama yalnızca yaklaşanı gösterir.

Dosyada **tek bir hata** bile olursa uygulama dosyanın tamamını yok sayar ve eski veriyle devam eder. Göndermeden önce JSON'u bir doğrulayıcıdan geçir.

GitHub önbelleği nedeniyle değişiklik kullanıcılara birkaç dakika içinde, uygulamanın en çok 6 saatlik yenileme aralığıyla ulaşır.
