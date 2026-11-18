# OVERLORD — Oda Konseptleri ve Modelleme Listesi

> Kaynak: `OVERLORD_GDD.md` (oda tablosu, soketler, loot, eşya havuzu, objective'ler).
> Bu belge 3D/art üretimi için çalışma listesidir. GDD'de karar olmayan her şey **öneri** olarak işaretlidir.

---

## 0. Okuma rehberi

### Etiketler (Tür sütunu)

| Kod | Anlamı | Modelleme gereksinimi |
|---|---|---|
| **S** | Statik | Sadece çarpışma, hareket etmez |
| **H** | Hafif fizik | Fırlatılabilir, tek elle alınır; basit convex collider, düşük poly |
| **A** | Ağır fizik | Sadece itilir/sürüklenir (Overlord ve oyuncu); itilince dolap önünü kapatabilmeli |
| **K** | Kırılabilir | Sağlam + kırık varyant (ya da parça seti) gerekir |
| **G** | Saklanma noktası | İçine girilir; dar görüş aralığı (aralık/yarık) olmalı, kapak fizikle açılır |
| **T** | Soket | Tuzak / Göz / yaratık yuvası. **Dolu ve boş hali birebir aynı görünmeli** |
| **L** | Loot | Alınabilir eşya (hazine, ekipman, bilgi) |
| **O** | Objective | Ana objective objesi |
| **Mum** | Işık kaynağı | Yanık + sönük durum, kibritle yakılır, alev shader'ı ileride mikrofona tepki verecek |

### Genel art yönü *(öneri)*

- **Stilize gotik, hafif abartılı oranlar.** Korku için karanlık ve gölge, komedi için tombul/okunaklı silüetler. Fizik objeleri uzaktan ne olduğu anlaşılacak kadar belirgin olmalı.
- **Ortak doku atlası + trim sheet** (taş, ahşap, demir, kumaş, altın/gümüş). Odalar aynı malzeme ailesini paylaşır; oda kimliği renk ve prop seçiminden gelir.
- **Düşük poly fizik objeleri.** Yemek Salonu gibi odalarda aynı anda onlarca fizik objesi olacak; ağ senkronu da var.
- **Kırık mobilya varyantı.** Otomatik döşemenin "detay" adımı kırık mobilya kullanıyor, bu yüzden ana mobilyaların çoğunun kırık hali gerekir.
- **Her oda 3–5 layout şablonundan** döşeniyor (MVP'de 3). Prop havuzu her odada birden fazla şablonu dolduracak kadar çeşitli olmalı.

---

## 1. Ortak kit (bütün odalarda kullanılır)

Bunlar her odadan önce yapılmalı; odaların %60–70'i bu kitle kurulur.

### 1.1 Modüler mimari

| Obje | Tür | Not |
|---|---|---|
| Taş duvar modülü (düz) | S | Grid hücresinin kenar boyunda |
| Duvar modülü, kapı açıklıklı | S | Her odanın 4 kenarı potansiyel kapı noktası; standart kemerli açıklık |
| Duvar modülü, pencereli | S | Sadece şatonun dış kenarındaki odalarda. Sivri kemer, demir parmaklık, ay ışığı girişi |
| Kapatılmış kapı yeri | S | Üretici kapıyı duvara çevirdiğinde. **Karar gerekli:** düz duvar mı (iz yok) yoksa örülmüş kemer mi (oyuncu "burada kapı vardı" der) |
| Köşe / kolon / payanda | S | Duvar birleşimleri |
| Ahşap kapı, demir kuşaklı | A | Menteşeli fizik; çarpar, gıcırdar. "Kilitle" için görünür sürgü/kilit animasyonu |
| Kapı kasası + eşik | S | |
| Zemin: taş döşeme | S | Varsayılan |
| Zemin: ahşap parke | S | Yatak Odası, Kütüphane, Gelin Odası |
| Zemin: mermer | S | Balo Salonu, Şapel, Galeri |
| Tavan: taş tonoz | S | Varsayılan, avize kancası noktalı |
| Tavan: ahşap kirişli | S | Yemek Salonu, Kütüphane |
| Yeraltı merdiven ağzı | S | Ana kattaki hücre: merdiven boşluğu, korkuluk, kapı. Kripta ve Mahzen'de farklı süsleme |
| Taş merdiven (aşağı inen) | S | Kripta ve Mahzen. Tabut taşınabilecek genişlikte ama dar hissettirmeli |
| Süpürgelik / pervaz trim'leri | S | Oda tipine göre renk varyantı |

### 1.2 Işık objeleri

| Obje | Tür | Not |
|---|---|---|
| Duvar apliği (tek mum) | S, Mum | En yaygın ışık |
| Masa şamdanı (3 kollu) | H, Mum | Fizikle devrilir, devrilince mum söner |
| Ayaklı şamdan (uzun) | A, Mum | İtilir, devrilir |
| Mum varyantları | Mum | Uzun, yarı erimiş, kütük; yanık ve sönük hal. Taşınamaz (GDD: taşınabilir mum yok) |
| Eriyik mum kümesi (zemin/raf) | S, Mum | Atmosfer; Şapel ve Kara Ayin için çok |
| Şömine | S | **Karar gerekli:** şömine ışığı fiziksel formu engeller mi? GDD'de sadece mum + fener sayılıyor. Öneri: şömineler sönük/küllü dekor olsun |

### 1.3 Soket objeleri (tuzak / Göz / yaratık)

Standart set: 1 avize · 2 zemin plakası · 2 duvar Göz'ü · 1 yaratık yuvası.

| Obje | Tür | Not |
|---|---|---|
| Avize | T, Mum | Zincirle asılı, düşebilir. Dolu/boş aynı. Küçük ve büyük varyant (Yemek Salonu'nda 2 adet) |
| Avize kırık hali (yerde) | K | Düştükten sonra kalan enkaz |
| Zemin plakası | T | Döşemeye gömülü taş; normal döşemeden ayırt edilmemeli ama oyuncu zamanla yerini öğrenebilmeli (çok hafif fark) |
| Duvar Göz'ü: portre | T, K | Çerçeve + tablo. Durumlar: normal, örtülü (örtü bezi), kırık. Gözlerin hafif kıpırdadığı belli belirsiz shader *(öneri)* |
| Duvar Göz'ü: gargoyle konsolu | T, K | Duvardan çıkan taş figür. Durumlar: normal, örtülü, kırık |
| Yaratık yuvası | T | Oda temasına göre görünüm: zemin ızgarası, duvar çatlağı, karanlık niş, lahit. Kapalıyken boşla aynı |

### 1.4 Ortak mobilya ve dekor havuzu

Otomatik döşemenin her odada kullanabildiği genel set.

| Obje | Tür | Not |
|---|---|---|
| Gardrop / dolap | G, A | Saklanma: kapakta yarık. Önüne ağır eşya itilince kapı açılmamalı (ihanet mekaniği) |
| Ayna (duvar) | K | Görünmez Overlord'u gösterir; Lanetli ve mimic'in yansıması yok → gerçek yansıma/planar reflection gerekli |
| Ayna (ayaklı) | A, K | Fizikle devrilir, kırılır |
| Zırh (dekor) | A | **Koridor'daki Mimic Zırh'la aynı model olmalı**; fark sadece niş içinde olması |
| Yan masa / konsol | A | |
| Sandalye (sade) | H | Devrilir, fırlatılır |
| Sandık (kapaklı) | A | İçinden loot çıkabilir |
| Vazo / testi | H, K | Kırılınca ses (dikkat çeker) |
| Mermer büst + kaide | A, K | |
| Halı / kilim | S | Kenarı kıvrık varyant |
| Duvar halısı (tapestry) | S | |
| Perde | S | Pencereli odalarda |
| Örümcek ağı | S | Mesh + decal, köşe/kapı üstü |
| Toz, moloz, taş parçası | S | Detay adımı |
| Kırık mobilya parçaları | S | Kırık sandalye, kırık masa ayağı |
| Kafes / zincir | S | Duvar dekoru |

### 1.5 Kapıcı tezgâhı

Kapıcı her round rastgele bir serbest odaya konur, bu yüzden **kendi başına taşınabilir bir köşe seti** olmalı.

| Obje | Tür | Not |
|---|---|---|
| Ahşap tezgâh / el arabası tezgâhı | S | Herhangi bir odaya sığacak boyut |
| Kepenk | S | Gece Yarısı'nın ilk çanında iner (animasyon) |
| Altın terazisi | S | Hazine bankalama anı için görsel geri bildirim |
| Defter (hesap kitabı) | S | Bankalanan puanın yazıldığı yer |
| Stok rafı (3–4 yuva) | S | Satılık eşyalar burada sergilenir; satılan yuva boşalır |
| Kapıcı'nın feneri | S, Mum | Odanın tanınır işareti |
| Kapıcı (karakter) | — | Açgözlü yaşlı uşak; karakter modeli, prop değil |

---

## 2. Odalar

Sıra: önce MVP odaları (8), sonra sonraki aşama (5).

---

### 2.1 Giriş Odası — MVP

**Konsept:** Şatonun dış kapısı, nöbetçi kulesi ve asma köprü. Grid'in dışında; içeride değil, eşikte durduğun hissi. Dışarıda yağmur ve sis, içeride ilk ve son güvenli ışık. Hem başlangıç hem kaçış noktası.

**Işık / palet:** Sıcak meşale turuncusu (içerisi) vs soğuk mavi gece (dışarısı). Oyunun en aydınlık yeri.

**Büktüğü kural:** Soketi yok, Overlord tehdit koyamaz. Gece Yarısı'ndan 3 dk sonra köprü kalkar.

| Grup | Obje | Tür | Not |
|---|---|---|---|
| Mimari | Asma köprü | S | Kalkış animasyonu (Gece Yarısı + 3 dk) — şatonun kapanışını görsel olarak anlatır |
| Mimari | Köprü zincirleri + vinç çarkı | S | Çark köprü kalkarken döner |
| Mimari | Demir parmaklıklı kale kapısı (portcullis) | S | Şatoya açılan iç kapı, grid giriş noktasına bağlanır |
| Mimari | Hendek / uçurum + sis | S | Köprünün altı; çıkış hissi |
| Mobilya | Başlangıç kiti sandığı | S | 3 Hazırlık Puanı draft'ı burada. Eşyalar sandıkta görünür dizilmeli (tebeşir, sarımsak, un, fener yağı, kutsal su, el aynası) |
| Mobilya | Fener askısı / raf | S | Herkese verilen sabit fener + kibrit |
| Mobilya | Nöbetçi masası, tabure | A, H | |
| Dekor | Duvar meşalesi | S, Mum | Mum sayılır mı? → ışık kuralına bağlanmalı |
| Dekor | Eski at arabası (dışarıda) | S | *(öneri)* Oyuncuların geldiği araba; lobi/round başı atmosferi |
| Dekor | Hanedan arması, sancak | S | |
| Dekor | Yağmur suyu birikintisi, çamur | S | |

---

### 2.2 Yatak Odası — MVP

**Konsept:** Overlord'un ini. Kadife, ağır perdeler, koyu kırmızı ve altın. Burası "yaşanan" bir oda: Drakula burada uyanır, av burada başlar. En değerli hazine buradadır ama en tehlikeli oda da burasıdır.

**Işık / palet:** Bordo, siyah, eski altın. Az mum, yoğun gölge.

**Büktüğü kural:** Av başlangıç noktası. Saklanma: yatak altı ve gardrop. Objective: **Kalbi Çal**.

| Grup | Obje | Tür | Not |
|---|---|---|---|
| Objective | Kalp kavanozu | O, H | Kavanozun içinde atan kalp: atış animasyonu + hafif kırmızı ışıma (ses yayar, yaratıkları çeker). Tek kişi taşır |
| Objective | Kalp kaidesi / sunak | S | Kavanozun durduğu yer; kalp alınınca boş kalan halka |
| Mobilya | Cibinlikli büyük yatak | G, S | Yatak altı saklanma → yerden yükseklik yeterli olmalı. Perdeli cibinlik |
| Mobilya | Büyük gardrop | G, A | Saklanma |
| Mobilya | Makyaj masası + **örtülü ayna** | S | *(öneri)* Drakula'nın aynası örtüyle kapalı (lore: yansıması yok). Örtü kaldırılabilir → aynaya dönüşür |
| Mobilya | Mücevher sehpası / kadife yastık | S | Drakula'nın mücevherlerinin durduğu yer |
| Mobilya | Berjer koltuk | A | |
| Mobilya | Şömine (sönük) | S | |
| Mobilya | Komodin | A | |
| Dekor | Ağır kadife perdeler | S | Pencere varsa |
| Dekor | Drakula'nın kendi portresi | T | Duvar Göz'ü olarak da çalışabilir |
| Dekor | Kurutulmuş gül, şarap kadehi, kitap | H | |
| Dekor | Ayı postu halı | S | |
| Loot | Drakula'nın mücevherleri | L | Oyunun en değerli hazinesi: taç, kolye, yüzük seti |
| Soket | Standart set | T | |

---

### 2.3 Şapel — MVP

**Konsept:** Şatonun tek kutsal yeri, terk edilmiş ama hâlâ korunan küçük bir kilise. Soğuk taş, çok sayıda mum, renkli cam (dış kenardaysa). İçeri giren herkes rahatlamalı; Overlord girerse sis formu titrer.

**Işık / palet:** Krem, beyaz mum ışığı, vitraydan düşen renkli ay ışığı. Oyunun "temiz" hissettiren tek odası.

**Büktüğü kural:** Güvenli oda. Yaratık giremez, Isırık işlemez, lanet temizlenir. Soketi yok.

| Grup | Obje | Tür | Not |
|---|---|---|---|
| Mimari | Vitray pencere | S | Sadece dış kenarda; renkli ay ışığı |
| Mimari | Apsis / sunak basamakları | S | |
| Etkileşim | Kutsal su kurnası | S | **Sınırlı kaynak:** su seviyesi görünür şekilde azalmalı (3–4 kademe) |
| Etkileşim | Lanet temizleme noktası (sunak) | S | Lanetlinin temizlendiği an için görsel efekt |
| Mobilya | Sunak + örtü | S | |
| Mobilya | Kilise sıraları | A | Ağır; itilebilir |
| Mobilya | Kürsü | S | |
| Mobilya | Günah çıkarma kabini | S | Dekor. **Saklanma yapılmamalı** (güvenli odada saklanmaya gerek yok) |
| Dekor | Büyük haç (duvar) | S | Alınamaz; ayrı loot haçı var |
| Dekor | Mum sehpaları, adak mumları | S, Mum | Odanın en çok mumu burada |
| Dekor | Aziz heykelleri | S | |
| Dekor | Dua kitapları, tespih | H | |
| Loot | Kutsal su şişesi | L | |
| Loot | Haç | L | İki elle tutulur |

---

### 2.4 Kripta ↓ — MVP

**Konsept:** Şatonun altındaki aile mezarlığı. Kemik duvarlar, lahitler, nem. **Mum yok** — ışık sadece oyuncuların fenerleri. Burası fener yağının bittiği yer olmamalı.

**Işık / palet:** Zifiri. Sadece fener konisi. Yeşilimsi gri taş, kemik beyazı.

**Büktüğü kural:** Işık (sadece fener). Tabutlar hazine, yaratık ya da saklanma olabilir. Objective: **Tabutu Çıkar**. Avize yok, +3 tabut soketi.

| Grup | Obje | Tür | Not |
|---|---|---|---|
| Objective | Objective tabutu | O, A | Diğerlerinden ayırt edilir: süslü, zincirli, 4 köşede tutamak. 2+ kişi taşır; merdivenden ve dar kapılardan geçebilecek ölçü |
| Mimari | İnen merdiven (ana kattan) | S | Dar, döner ya da düz |
| Mimari | Mezar nişleri (duvar gözleri) | S | Raf gibi, içinde sarılı ceset/kemik |
| Mimari | Kemik duvar (ossuary) | S | Kafatası dizileri |
| Mimari | Alçak tonoz, kemerli geçitler | S | |
| Soket | Soket tabutu ×3 | T, G | Yaratık çıkışı. Dolu/boş aynı görünmeli |
| Saklanma | Saklanma tabutu | G, A | İçinde hazine, yaratık ya da boşluk; kapak levyeyle zorlanabilir |
| Mobilya | Taş lahit (kapaklı) | S | Kapak kaydırılır |
| Mobilya | Kırık tabut | K | |
| Dekor | Sönük mum dipleri, eski şamdan | S | **Yakılamaz** (oda kuralı: mum yok) — sadece hikâye |
| Dekor | Kemik, kafatası yığını | H | Ayakla tekmelenir, ses yapar |
| Dekor | Örümcek ağı (yoğun) | S | |
| Dekor | Su damlası, nem lekesi | S | |
| Loot | Mezar yüzükleri | L | |
| Loot | Altın sikke kesesi | L | |
| Loot | Kazık | L | |
| Loot | Levye | L | |

---

### 2.5 Şarap Mahzeni ↓ — MVP

**Konsept:** Soğuk, nemli, kemerli bir mahzen. Fıçılar, raflar dolusu şişe, dökülmüş şarap. Herkesin nefesi buhar yapar, bu yüzden Overlord'un buhar ipucu burada işe yaramaz.

**Işık / palet:** Koyu mavi soğukluk + şarap kırmızısı lekeler. Az mum.

**Büktüğü kural:** Nefes (soğuk, buhar). Dökülen şarap zemini kaydırır. +2 fıçı soketi. Objective: **Şarap Mahzeni** (kırılgan şişelerle kota).

| Grup | Obje | Tür | Not |
|---|---|---|---|
| Objective | Kota şişesi | O, H, K | Kırılgan; düşünce kırılır. Normal şişeden ayırt edilmeli (mühür/etiket) |
| Objective | Teslim kasası / sepet | S | **Karar gerekli:** kota nereye teslim ediliyor? (Mahzen içinde mi, Giriş'te mi) |
| Mimari | İnen merdiven | S | |
| Mimari | Kemerli tonoz | S | Buzlanma decal'leri |
| Soket | Soket fıçısı ×2 | T, A | Yuvarlanan fıçı tuzağı; dolu/boş aynı |
| Mobilya | Fıçı (büyük, yatık) | S | Rafta duran |
| Mobilya | Fıçı (küçük) | A | Yuvarlanabilir |
| Mobilya | Şarap rafı (duvar) | S | Şişe yuvalı; şişeler ayrı fizik objesi |
| Mobilya | Ahşap kasa / sandık | A | |
| Mobilya | Tadım masası | A | |
| Mobilya | Fıçı tıpası, musluk | S | Sızıntı efekti |
| Saklanma | Boş büyük fıçı | G | *(öneri)* Saklanma noktası; buhar kapaktan sızar (GDD) |
| Dekor | Dökülmüş şarap birikintisi | S | **Kaygan zemin** decal + collider |
| Dekor | Kırık şişe camı | S | |
| Dekor | Asılı sarımsak örgüsü | L | Loot olarak da alınır |
| Dekor | Buz sarkıtı, kırağı | S | Soğukluk hissi |
| Loot | Eski şarap şişesi (değerli) | L, K | Kırılgan hazine |
| Loot | Un torbası | L | |
| Loot | Fener yağı | L | |
| Loot | Levye | L | |
| VFX | Nefes buharı (herkes için) | — | Odanın tanımlayıcı efekti |

---

### 2.6 Koridor — MVP

**Konsept:** Dar, uzun, karanlık bir geçit. Duvarlar zırhlar ve portrelerle dolu. Burada itilmek veya çelme yemek gerçekten tehlikeli.

**Işık / palet:** Aralıklı aplik mumları, aralarda karanlık. Kırmızı uzun halı.

**Büktüğü kural:** Dar alan, itme/çelme tehlikeli. Avize yok. +2 zırh nişi (Mimic Zırh), +1 Döner Duvar.

| Grup | Obje | Tür | Not |
|---|---|---|---|
| Mimari | Dar koridor duvar modülü | S | Normal duvarlardan daha yakın |
| Soket | Zırh nişi ×2 | T | Mimic Zırh. Niş içindeki zırh, dekor zırhla **aynı model** |
| Soket | Döner Duvar | T | Dönen duvar paneli + mekanizma; kapalıyken normal duvardan ayırt edilmemeli |
| Mobilya | Konsol masa | A | |
| Mobilya | Bekleme bankı | A | |
| Dekor | Uzun koşu halısı | S | |
| Dekor | Portre sırası | S / T | Bir kısmı Göz soketi |
| Dekor | Dekor zırhlar | A | |
| Dekor | Kalkan + çapraz kılıç (duvar) | S | |
| Dekor | Vazo, büst | H/A, K | Koridorda devrilen vazo = klasik ortam olayı |
| Loot | Tebeşir, fener yağı, kibrit, bilye torbası | L | Yaygın eşyalar |

---

### 2.7 Kütüphane — MVP

**Konsept:** Tavana kadar raflar, raf labirenti, dar görüş. Sürekli kitap düşer; bir raf gizli geçittir. Bilgi odası: kat planı sayfaları ve Drakula'nın Günlüğü burada.

**Işık / palet:** Sıcak kahve, eski kâğıt sarısı; mumlar raf aralarında seyrek.

**Büktüğü kural:** Belirsizlik. Görüş kısa, kitap düşme olayı en sık burada. Rastgele bir raf gizli geçit. +2 raf arkası soketi.

| Grup | Obje | Tür | Not |
|---|---|---|---|
| Mobilya | Uzun kitap rafı (duvar) | S | Modüler; labirent kurulabilmeli |
| Mobilya | Serbest duran raf (iki yüzlü) | S | Labirentin ana parçası |
| Mobilya | Gizli geçit rafı | S | Dönen/açılan raf; kapalıyken normal raftan ayırt edilmemeli |
| Soket | Raf arkası ×2 | T | Kitap yağmuru tuzağı / gizli geçit. Dolu/boş aynı |
| Mobilya | Raylı kütüphane merdiveni | A | Kayar (fizik komedisi) |
| Mobilya | Okuma masası + sandalye | A, H | |
| Mobilya | Kürsü (Günlük için) | S | Nadir loot standı |
| Mobilya | Dünya küresi (ayaklı) | A | Döner, yuvarlanır |
| Mobilya | Okuma koltuğu | A | |
| Dekor | Kitap (tekil) ×5–6 varyant | H | Düşen kitap olayı; düşük poly, çok kopya |
| Dekor | Kitap yığını | H | Devrilir |
| Dekor | Parşömen, rulo harita | H | |
| Dekor | Mürekkep hokkası, tüy kalem | H | |
| Dekor | Yerde açık kitap, savrulmuş sayfalar | S | |
| Loot | Nadir kitap | L | Hazine; normal kitaptan ayırt edilmeli (deri cilt, parlama) |
| Loot | Kat planı sayfası | L | |
| Loot | Drakula'nın Günlüğü | L | Nadir; özel kapak |
| Loot | Simya notu | L | |

---

### 2.8 Yemek Salonu — MVP

**Konsept:** Uzun bir ziyafet masası, yarım bırakılmış (ve çürümüş) bir şölen. Oyunun fizik komedisi odası: fırlatılacak her şey burada. İki avizeyle en büyük tuzak odası.

**Işık / palet:** Altın ve gümüş parıltı, yeşilimsi çürük yemek tonları.

**Büktüğü kural:** Fizik. En çok fırlatılabilir eşya burada. 2 avize.

| Grup | Obje | Tür | Not |
|---|---|---|---|
| Mobilya | Uzun ziyafet masası | S | Masa üstü fizik objeleri için geniş yüzey; altına çömelinebilir *(öneri: saklanma değil, sadece sığınak)* |
| Mobilya | Yüksek sırtlı sandalye ×10–12 | H | Masa başı; Overlord'un devirme favorisi |
| Mobilya | Ev sahibi tahtı (masa başı) | A | |
| Mobilya | Büfe / vitrinli dolap | A, G? | Büyükse saklanma noktası olabilir |
| Mobilya | Servis arabası | A | Tekerlekli, itilince kayar |
| Mobilya | Şömine (büyük) | S | |
| Soket | Avize ×2 | T | |
| Fizik | Tabak, kâse | H, K | Çok kopya |
| Fizik | Kadeh, sürahi | H, K | |
| Fizik | Servis tepsisi + kapağı (cloche) | H | Kapağın altından ne çıkacağı belli değil |
| Fizik | Kızarmış domuz / tavuk (çürük) | H | Komedi objesi |
| Fizik | Meyve, ekmek, peynir tekerleği | H | Peynir tekerleği yuvarlanır |
| Fizik | Masa şamdanı | H, Mum | |
| Dekor | Duvara asılı geyik/yaban domuzu başı | S / T | Gargoyle yerine Göz olabilir *(öneri)* |
| Dekor | Masa örtüsü | S | Çekilebilir *(öneri, kumaş fiziği pahalıysa statik)* |
| Loot | Gümüş çatal bıçak takımı | L | |
| Loot | Gümüş şamdan | L | Ağır hazine, iki elle |
| Loot | Sarımsak | L | |
| Loot | Yemek zili | L | Zil eşyası |
| Loot | Un torbası | L | |

---

### 2.9 Balo Salonu — Sonraki aşama

**Konsept:** Duvarları ayna kaplı, devasa, boş bir balo salonu. Hayalet bir baloda kalmış gibi: dağılmış maskeler, devrilmiş kadehler, köşede sessiz bir org. Saklanacak yer yok; aynalar her şeyi gösterir. Overlord için tehlikeli oda.

**Işık / palet:** Kristal avizenin soğuk beyazı, altın varak, pembe-mor kadife. Aynalar ışığı çoğaltır.

**Büktüğü kural:** Ayna. +4 ayna soketi (ayna kırma tuzağı). Saklanma noktası **yok**. Objective: **Kara Ayin** (4 mumu aynı anda yakmak).

| Grup | Obje | Tür | Not |
|---|---|---|---|
| Objective | Ayin şamdanı ×4 | O, S, Mum | Odanın 4 uzak köşesinde; grup bölünmek zorunda. Yakılınca belirgin renk değişimi |
| Objective | Zemindeki ayin çemberi | S | Mermer zemine işlenmiş sembol; mumlar yandıkça parlar |
| Mimari | Ayna duvar paneli | S, K | Duvarların büyük kısmı; performans için planar reflection sayısı sınırlanmalı |
| Soket | Ayna soketi ×4 | T, K | Ayna kırma tuzağı; sağlam hali panelle aynı |
| Mimari | Müzisyen balkonu / galeri | S | |
| Mimari | Mermer kolonlar | S | |
| Mobilya | Org ya da klavsen | S | Ortam olayı: kendiliğinden tek nota |
| Mobilya | Duvar dibi sandalyeleri | H | Az sayıda |
| Mobilya | İkram masası (devrik) | A | |
| Soket | Büyük kristal avize | T | |
| Dekor | Dağılmış balo maskeleri | H | |
| Dekor | Devrik kadehler, konfeti | H / S | |
| Dekor | Kadife kordonlar, çiçek düzenlemesi | S | |
| Loot | Mücevher | L | |
| Loot | Balo maskesi (değerli) | L | Dekor maskelerden ayırt edilmeli |
| Loot | El aynası | L | |
| Loot | Bilye torbası | L | |

---

### 2.10 Portre Galerisi — Sonraki aşama

**Konsept:** Uzun bir sergi salonu; duvarlar ataların portreleriyle dolu ve hepsi seni izliyor. Overlord için bedava Gözler. Portrelerden biri "gerçek"; yanlışını alan alarmı çalar.

**Işık / palet:** Müze ışığı gibi tablolara vuran mum spotları, aralarda karanlık. Koyu yeşil duvar kâğıdı, altın çerçeveler.

**Büktüğü kural:** Gözler. 6 duvar soketi. İnsanlar portreleri örtebilir. Objective: **Gerçek Portre** (20 portreden biri).

| Grup | Obje | Tür | Not |
|---|---|---|---|
| Objective | Gerçek portre | O, H | Duvardan alınıp taşınır. Diğerlerinden ayırt etmek **zor** ama mümkün olmalı (ipucu detayı) |
| Objective | Sahte portre ×19 | H | Duvardan alınabilir; çerçeve boyu + tablo içeriği varyantlı. **Portre üretici sistemi** öneri: 4–5 çerçeve × 10+ yüz dokusu |
| Etkileşim | Alarm (çan / çığlık atan portre) | S | Yanlış portre alındığında |
| Soket | Duvar Göz'ü ×6 | T | En çok Göz burada |
| Mobilya | Galeri bankı (ortada) | A | |
| Mobilya | Kadife kordon + direk | H | Devrilir |
| Mobilya | Kaideli büst | A, K | |
| Dekor | Örtülü tablo (sergi dışı) | S | Örtü altından ne çıkacak? |
| Dekor | Boş çerçeve, duvara dayalı tablolar | S | |
| Dekor | Tablo spot mumları | S, Mum | |
| Loot | Küçük tablo | L | Hazine |
| Loot | Örtü bezi | L | |

---

### 2.11 Gelin Odası — Sonraki aşama

**Konsept:** Drakula'nın gelinlerinden birinin odası. Beyaz dantel, solmuş çiçekler, tozlu bir düğün. Romantik ve ürkütücü. Saklanma noktaları en çok burada. Kurtarılacak NPC gelin de burada.

**Işık / palet:** Kirli beyaz, pudra pembesi, solgun lavanta. Yumuşak mum ışığı, tül perdeler.

**Büktüğü kural:** Saklanma (dolap, yatak altı). Objective: **Gelini Kurtar**.

| Grup | Obje | Tür | Not |
|---|---|---|---|
| Objective | Gelin (NPC) | O | Karakter modeli; kendi kafasına gezer, Overlord ele geçirebilir |
| Mobilya | Tül cibinlikli yatak | G, S | Yatak altı saklanma |
| Mobilya | Gardrop ×2 | G, A | En çok saklanma noktası |
| Mobilya | Paravan | A | Arkası yarı saklanma *(öneri)* |
| Mobilya | Makyaj masası + üç kanatlı ayna | S, K | |
| Mobilya | Divan / şezlong | A | |
| Mobilya | Çeyiz sandığı | A | |
| Dekor | Gelinlik giydirilmiş manken | A | *(öneri)* Karanlıkta gelinle karıştırılır, oyuncuyu kandırır |
| Dekor | Duvak, eldiven, buket (solmuş) | H | |
| Dekor | Müzik kutusu | H | Ortam olayı: kendiliğinden çalar |
| Dekor | Bebek / porselen oyuncak | H | |
| Dekor | Mektup yığını, mum mühür | H | |
| Loot | Mücevher kutusu | L | |
| Loot | Anahtar | L | |

---

### 2.12 Simya Laboratuvarı — Sonraki aşama

**Konsept:** Drakula'nın ölümsüzlük deneyleri. Fokurdayan imbikler, renkli sıvılar, kavanozdaki tuhaf örnekler. Her şey cam, her şey kırılır, her kırılış ses yapar.

**Işık / palet:** Renkli iksir ışımaları (yeşil, mor, turuncu), ocak kızıllığı. Kaotik ve dumanlı.

**Büktüğü kural:** Eşya. Etkisi bilinmeyen iksirler, kırılınca ses yapan camlar.

| Grup | Obje | Tür | Not |
|---|---|---|---|
| Mobilya | Simya tezgâhı | S | |
| Mobilya | İmbik (alembik) düzeneği | S, K | |
| Mobilya | Simya ocağı (atanor) | S | Kızıl ışık: ışık kuralına bağlanmalı |
| Mobilya | Kazan | A | |
| Mobilya | Kavanoz rafı | S | |
| Mobilya | Kaide üstünde kristal küre | H, K | |
| Fizik | Cam şişe, balon joje, deney tüpü | H, K | Çok kopya, kırılma sesi kritik |
| Fizik | Havan + havan eli | H | |
| Fizik | Kafatası, kum saati | H | |
| Dekor | Kavanozdaki örnekler (göz, yarasa, organ) | H, K | |
| Dekor | Astroloji haritaları, simya sembolleri (duvar) | S | |
| Dekor | Asılı kurutulmuş otlar | S | |
| Dekor | Dökülmüş renkli sıvı lekesi | S | |
| Loot | İksir şişesi ×6 renk | L, K | Renk–etki eşleşmesi seed'le değişir → **şişe şekli tek, renk parametrik** |
| Loot | Simya altını | L | |
| Loot | Flaş tozu | L | Nadir |

---

### 2.13 Kule Merdiveni — Sonraki aşama (çok katlı şato)

**Konsept:** Dar, döner taş merdiven. Mazgal pencerelerden rüzgâr ıslık çalar. Kırık korkuluk = ragdoll düşüş. *(Öneri: çan saatinin çanları burada asılı olabilir; Gece Yarısı çanları bu odadan duyulur.)*

**Işık / palet:** Dar aydınlıklar, mazgallardan ay ışığı şeritleri.

**Büktüğü kural:** Dikey geçiş, ragdoll düşüş.

| Grup | Obje | Tür | Not |
|---|---|---|---|
| Mimari | Döner taş merdiven modülü | S | Katlar arası; tekrar eden modül |
| Mimari | Ara sahanlık | S | |
| Mimari | Mazgal pencere | S | |
| Mimari | Kırık basamak / boşluk | S | |
| Mobilya | Korkuluk (sağlam + kırık) | S, K | |
| Dekor | Halat, zincir, makara | S | |
| Dekor | Büyük çan + çan mekanizması | S | *(öneri)* |
| Dekor | Kuş/yarasa yuvası, tüyler | S | |

---

## 3. Taşınabilir eşyalar (loot, ekipman, hazine)

Oda dışında da kullanıldıkları için ayrıca listelenmiştir. Hepsi **H** (hafif fizik) ve elde tutuş pozuna ihtiyaç duyar. Haç ve ağır hazineler iki elle tutulur.

### 3.1 Ekipman

| Eşya | Not |
|---|---|
| Fener | Kemere takılabilir hali de olmalı (ışık daralır). Yağ seviyesi göstergesi, titreme |
| Kibrit kutusu + kibrit | Çakma animasyonu |
| Fener yağı | Küçük teneke / şişe |
| Flaş tozu | Kese ya da kavanoz; patlama VFX |
| El aynası | Gerçek yansıma gerekli (küçük render target) |
| Un torbası | Serpme VFX + ayak izi decal'i |
| Bilye torbası | Dökülen bilyeler (çok sayıda küçük fizik objesi → optimize) |
| Tebeşir | Zemin/duvar ok decal'i |
| Kutsal su şişesi | |
| Sarımsak (örgü) | Yere koyulunca bölge |
| Haç | İki elle |
| Kazık | Ahşap |
| Gümüş Kazık | Sadece Kapıcı; normal kazıktan belirgin şekilde farklı |
| Anahtar | |
| Levye | |
| Yemek zili | |
| Örtü bezi | Göz'ün üstüne atılınca örtülü hal |
| Kat planı sayfası | Okununca ekranda harita |
| Simya notu | |
| Drakula'nın Günlüğü | |
| İksir şişesi | Renk parametrik (bkz. Simya) |

### 3.2 Hazine

| Hazine | Oda | Ağırlık |
|---|---|---|
| Drakula'nın mücevherleri | Yatak Odası | Tek el (en değerli) |
| Mezar yüzükleri | Kripta | Tek el |
| Altın sikke kesesi | Kripta | Tek el |
| Eski şarap şişesi | Mahzen | Tek el, kırılgan |
| Mücevher | Balo Salonu | Tek el |
| Balo maskesi | Balo Salonu | Tek el |
| Nadir kitap | Kütüphane | Tek el |
| Gümüş çatal bıçak takımı | Yemek Salonu | Tek el |
| Gümüş şamdan | Yemek Salonu | **İki el** (çelmeyle düşer) |
| Küçük tablo | Portre Galerisi | İki el *(öneri)* |
| Mücevher kutusu | Gelin Odası | Tek el |
| Simya altını | Simya Lab. | Tek el |

---

## 4. Üretim önceliği *(öneri)*

| Sıra | Paket | İçerik |
|---|---|---|
| 1 | Ortak kit | Modüler duvar/zemin/kapı/pencere, ışık objeleri, soket objeleri, gardrop, ayna, zırh |
| 2 | Çekirdek ekipman | Fener, kibrit, başlangıç kiti eşyaları |
| 3 | MVP objective odaları | Yatak Odası (Kalbi Çal), Kripta (Tabutu Çıkar), Şapel, Giriş Odası |
| 4 | MVP serbest odalar | Koridor, Kütüphane, Yemek Salonu, Şarap Mahzeni |
| 5 | Kapıcı tezgâhı | MVP'de var |
| 6 | Sonraki aşama | Balo Salonu, Portre Galerisi, Gelin Odası, Simya Lab., Kule Merdiveni |

**Kaba sayım (MVP):** ~25 ortak kit parçası + ~90 oda propu + ~20 taşınabilir eşya + ~10 hazine. Kırık varyantlar ve renk/doku varyantları bunun üstüne.

---

## 5. Art tarafında karar bekleyenler

1. **Şömine / meşale / simya ocağı ışığı** fiziksel formu engeller mi? GDD sadece mum + fener diyor. Engellemiyorsa bu kaynaklar oyuncuyu yanıltır (iyi ya da kötü).
2. **Kapatılmış kapı yeri** düz duvar mı, örülmüş kemer mi?
3. **Şarap kotası** nereye teslim ediliyor?
4. **Grid hücresi boyutu** ve oda büyüklükleri: Balo Salonu ve Yemek Salonu tek hücre mi, 2 hücre mi? Modüler duvar ölçüsü buna bağlı.
5. **Zemin plakası ipucu:** Oyuncular soket yerlerini "zamanla öğrenir" deniyor. Plaka hiç belli olmasın mı, yoksa çok hafif bir doku farkı mı olsun?
6. **Göz'lerin canlı hali:** Overlord bir portreden bakarken insanlara herhangi bir belirti (göz kıpırtısı) gösterilsin mi?
