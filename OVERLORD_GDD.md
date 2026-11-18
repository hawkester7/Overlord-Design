# OVERLORD — Game Design Document

2026-11-03 · @Gökberk

## Genel bakış

Overlord, bir oyuncunun Drakula benzeri Overlord, diğerlerinin insan olduğu asimetrik bir friend-slop korku oyunu. Her maç gotik bir şato dungeon'ı otomatik üretilir; Overlord maç öncesi içine tuzaklarını ve yaratıklarını yerleştirir. İnsanlar süre bitmeden objective'i tamamlayıp kaçmaya çalışır.

- **Ton:** Korku önde, komedi mekaniklerden kendiliğinden doğar. Şaka yazılmaz, komik şekilde bozulan sistemler kurulur.
- **Tema:** Drakula şatosu. Mumlar, portreler, zırhlar, tabutlar, aynalar.
- **Referanslar:** Lethal Company, R.E.P.O., Mimicry.
- **Yapı:** Oyun bireysel. Herkes sırayla Overlord olur, seans sonunda tek kazanan çıkar. İnsanlar round içinde birlikte çalışır ama birbirinin kuyusunu da kazar.

### Temel tasarım prensipleri

1. **Belirsizlik:** Her ipucunun en az iki açıklaması olmalı. "Overlord mu, şato mu?" sorusu gerilimin kaynağı.
2. **Bilinen tehdit:** Herkes Overlord'un ability havuzunu bilir ama hangilerini seçtiğini bilmez. Korku sürprizden değil, uzak güçlerin avı korkutup hazırlaması, yakın güçlerin ise öldürmesinden gelir.
3. **Aynalar gerçeği gösterir:** Görünmez Overlord, Lanetliler ve mimic'ler aynayla ifşa olur.
4. **Her eşyanın iki yüzü:** Her eşyanın bir yardım, bir de ihanet kullanımı var. Doğrudan PvP öldürme yok.
5. **Ezber yok:** Şato her round'da, yani her yeni Overlord'la birlikte yeniden üretilir; odalar her round otomatik döşenir.
6. **Round'lar eşit:** Round'dan round'a para ya da eşya taşınmaz, sadece puan taşınır. İlk ve son Overlord aynı güçteki insanlarla karşılaşır.

## Seans ve round yapısı

Bir seans, oyuncu sayısı kadar round'dan oluşur ve her oyuncu bir kez Overlord olur. Bir round yaklaşık 18 dakika sürer.

| Faz | Süre | Overlord | İnsanlar |
|---|---|---|---|
| 0. Kontrat | ~10 sn | Ana objective'i görür | Ana objective'i görür |
| 1a. Şato üretimi | Anlık | Oyun şatoyu üretir: odalar, kapılar, varsa yem oda | — |
| 1b. Kurulum | ~2 dk | Haritayı ilk kez görür. Tuzak ve yaratık yerleştirir, yem oda varsa objective'in hangisinde olacağını seçer, ability seçer. Kapıcı'nın yerini ve stoğunu görür. Gold burada biter | Başlangıç kiti seçimi (kör draft, bkz. Ekonomi) |
| 1c. Otomatik döşeme | Anlık | Oyun eşya, mobilya, ayna, mum, saklanma noktası ve loot yerleştirir | — |
| 1d. Av öncesi | ~10 sn | — | Gizli yan görevlerini görür |
| 2. Av | ~12 dk (21:00 → 24:00) | Yatak Odası'nda başlar. Görünmez gezer, ability ve fizik kullanır, konuşur | Objective'i bulur, loot toplar, gizli görevleri yapar, kaçar |
| 2b. Gece Yarısı | 3 dk | Cooldown'lar yarıya iner, Tezahür açılır | Son şans; köprü kalkmadan Giriş Odası'na dönmek zorunda |
| 3. Sonuç | ~1 dk | Puanlar, gizli görevlerin ifşası | Aynı |

Süreler ilk değerlerdir, playtest ile ayarlanacak.

## Şato üretimi ve kurulum

Overlord şatoyu kurmaz. Şato her round'da (her yeni Overlord'la) sistem tarafından yeniden üretilir; Overlord maç öncesinde sadece tuzaklarını ve yaratıklarını yerleştirir. Odaların içiyle de uğraşmaz, içini oyun döşer.

**Neden oda inşası yok (2026-11-07):** Şatonun karmaşık ve sıkışık hissetmesi için inşa alanını daraltmak gerekiyordu. Ama alan daraldıkça oda dizmek gerçek bir karar olmaktan çıktı; aşama hiçbir şeye hizmet etmeden round'u uzatıyordu. Sıkışıklığı artık üretici sağlıyor, Overlord'un yaratıcılığı tuzaklarda ve yaratıklarda kalıyor.

- Şato her maç yeni olduğu için Overlord da onu ilk kez kurulumda görür. Ezber layout ya da meta inşa oluşmaz.
- Overlord kurulum boyunca haritanın tamamını görür, insanlar görmez. Bu Overlord'un ev sahibi avantajıdır; insanlar şatoyu gezerek ve kat planı sayfalarıyla öğrenir.

### Şato üretimi

- Şato kare bir grid üstüne üretilir. Grid boyu oyuncu sayısına göre büyür (örnek: 3 insan için 4x4, 5 insan için 5x5). Artık Overlord'a inşa alanı bırakmak gerekmediği için grid oda sayısına göre dar tutulabilir.
- **Giriş Odası** grid'in dışındadır. Kapısı grid'in kenarındaki sabit bir giriş noktasına açılır.
- **Yatak Odası** giriş noktasının tam karşısına, grid'in öbür kenarına konur.
- Grid'deki her oda 4 kenarında da potansiyel kapı noktası taşır. Yan yana gelen iki odanın ortak kenarında kapı varsayılan olarak açıktır; üretici bir kısmını duvara çevirir (bkz. Karmaşıklık).
- **Kripta ve Mahzen** bu kuralın dışındadır. Yeraltında oldukları için grid'de sadece merdiven ağzının hücresini kaplarlar.
- Yol garantisi: girişten her odaya ulaşılabilir. Üretici bunu sağlamayan bir şatoyu atıp yeniden üretir.
- Pencereler varsayılan değildir. Layout'a göre şatonun dış duvarına bakan odaların dış kenarlarında otomatik pencere oluşur, içeride kalan odalarda oluşmaz. Yeraltındaki Kripta ve Mahzen'de pencere yoktur. Pencereden giren ay ışığı odayı hafif aydınlatır ama Overlord'un fiziksel forma geçmesini engellemez.

#### Oda seti

- Her şatoda: Yatak Odası + Şapel + diğer objective odaları + insan sayısı kadar serbest oda.
- Örnek: MVP'de 3 insan için 6 oda (Yatak Odası, Şapel, Kripta + 3 serbest). Tam oyunda 3 insan için 10, 5 insan için 12 oda.
- Serbest odaları üretici seçer: Koridor, Kütüphane, Yemek Salonu, Simya Laboratuvarı ya da bir objective odasının ikinci kopyası (yem oda, bkz. Kurulum).
- Tekrar sınırı: aynı tipten en fazla 2 oda. Balo Salonu, Şapel ve Yatak Odası en fazla 1.
- Ekstra oda yoktur; oda sayısını oyuncu sayısı belirler.

#### Karmaşıklık *(öneri, playtest'le ayarlanacak)*

Üreticinin amacı şatonun dar, dolambaçlı ve kafa karıştırıcı hissettirmesi.

- **Sıkı yerleşim:** Odalar grid'e dağınık değil, birbirine yapışık kümelenir.
- **Dolambaçlı yol:** Giriş'ten Yatak Odası'na düz bir hat olmaz; üretici kapıları duvara çevirerek en kısa yolu uzatır.
- **Döngü ve çıkmaz:** Her şatoda en az bir döngü (iki farklı yoldan ulaşılan bölge) ve birkaç çıkmaz olur. Döngü kaçışa ve kovalamacaya, çıkmaz paniğe yarar. Kripta ve Mahzen zaten çıkmazdır.
- **Şapel uzakta:** Şapel ne girişe ne Yatak Odası'na bitişik olur. Güvenli odaya ulaşmak bir yolculuk olmalı.

### Kurulum: tuzaklar ve yaratıklar

Overlord kurulumda üretilmiş şatoyu görür ve ~2 dakika içinde tehditlerini yerleştirir. Objective'i Kontrat'tan beri bilir. Objective eskiden ezber oda inşasını önlemek için Overlord'dan gizleniyordu; oda inşası kalkınca bu sebep de kalktı.

- Her oda tipinin soket yerleri sabittir (bkz. Odalar). Tuzaklar soketlere, yaratıklar yaratık yuvalarına konur. Hepsi Gold'la alınır.
- **Yem oda:** Üretici bir objective odasının ikinci kopyasını çıkardıysa, objective'in hangisinde olacağını Overlord seçer. Diğer kopya yem olur.
- Objective odasına konan tuzak ve yaratıklar 2 kat Gold tutar. Overlord objective'i baştan bildiği için bu kural daha da önemli: tek bir odanın kaleye çevrilmesini engeller.
- Overlord bu aşamada açtığı ability havuzundan av fazı için 3–4 aktif ability seçer. İnsanlar bu seçimi görmez.

**Gold:** Gold'un tamamı artık tuzak ve yaratıklara gider (ekstra oda alımı yok), bu yüzden toplam Gold miktarı yeniden dengelenmeli. Harcanmayan Gold yanar ve puana dönüşmez. Av sırasında Overlord Gold kullanmaz, tek kaynağı cooldown'lardır.

### Otomatik döşeme

Döşeme kurulumdan sonra olur ve tamamen sistemin işidir. Overlord'un müdahalesi ve reroll yoktur.

1. **Layout şablonu:** Her oda tipinin 3–5 iskeleti vardır. Soketler her şablonda aynı yerdedir.
2. **Prop seti:** Masalar, mumlar, zırhlar, aynalar, dolaplar, saklanma noktaları ve loot rastgele yerleşir.
3. **Detay ve ışık:** Mum sayısı, kırık mobilya, sis yoğunluğu. Aynı oda bir maçta aydınlık, ötekinde zifiri olabilir.

Overlord tuzakları koyarken odanın son halini bilmez. Aynaların, dolapların ve loot'un nerede çıktığını av başlayınca Gözler'den öğrenir. Döşeme tuzaklı soketlerin önünü kapatmaz, ama boş soketlere de aynı şekilde davranır ki dolu soketler belli olmasın. Oyuncular soketlerin yerini zamanla öğrenir, ama hangisinin dolu olduğunu bilemez.

## Odalar

Oyunda 13 oda tipi var, MVP'de 8 tanesi. Her ana oda oyunun bir sistemini büker (ışık, ayna, nefes, saklanma, Gözler, fizik, eşya). Böylece oyuncu odaya girdiği anda neye dikkat edeceğini bilir.

| Oda | Kategori | Büktüğü kural | Objective | MVP |
|---|---|---|---|---|
| Giriş Odası | Sabit, grid dışı | Başlangıç, ekipman sandıkları, köprü ve kaçış. Soketi yok, Overlord buraya tehdit koyamaz | — | Evet |
| Yatak Odası | Sabit, sistem koyar | Overlord'un ini ve av başlangıcı. Yatak altı ve gardropta saklanma | Kalbi Çal | Evet |
| Şapel | Sabit, sistem koyar | Güvenli oda: yaratık giremez, Isırık işlemez, lanet temizlenir, kutsal su kaynağı. Overlord girerse sis formu titrer | — | Evet |
| Kripta ↓ | Objective, yeraltı | **Işık:** mum yok, sadece fener. Tabutlar hazine, yaratık ya da saklanma yeri olabilir | Tabutu Çıkar | Evet |
| Şarap Mahzeni ↓ | Objective, yeraltı | **Nefes:** soğuk, herkesin nefesi buhar yapar ve Overlord ipucu bozulur. Dökülen şarap zemini kaydırır | Şarap Mahzeni | Evet |
| Balo Salonu | Objective | **Ayna:** duvarlar ayna kaplı, saklanacak yer yok. Overlord için tehlikeli oda | Kara Ayin | — |
| Portre Galerisi | Objective | **Gözler:** duvarlar portreyle dolu, Overlord'a bedava Göz. İnsanlar portreleri örtebilir | Gerçek Portre | — |
| Gelin Odası | Objective | **Saklanma:** dolap ve yatak altı noktaları | Gelini Kurtar | — |
| Koridor | Serbest | Dar, itme ve çelme çok tehlikeli. Portre ve zırhlar için doğal yer | — | Evet |
| Kütüphane | Serbest | **Belirsizlik:** raf labirenti, görüş kısa, kitap düşme olayı en sık burada. Rastgele bir raf gizli geçit olur | — | Evet |
| Yemek Salonu | Serbest | **Fizik:** en çok fırlatılabilir eşya burada. Fizik komedisinin ana odası | — | Evet |
| Simya Laboratuvarı | Serbest | **Eşya:** etkisi bilinmeyen iksirler, kırılınca ses yapan camlar | — | — |
| Kule Merdiveni | Serbest | Dikey geçiş, ragdoll düşüş. Çok katlı aşamada eklenir | — | — |

### Yeraltı odaları (Kripta, Mahzen)

- Kapıları ana katta, odaları merdivenle aşağıdadır. Grid'de sadece merdiven ağzının hücresini kaplarlar ve birbirlerinin üstüne binemezler.
- Çıkmaz odalardır. Kapı kilitlenirse (Kilitle ability'si) aşağıdakiler mahsur kalır.
- Tabutu Çıkar'da tabut merdivenden yukarı taşınmak zorundadır.
- Aşağıdaki ses yukarıya boğuk gelir.

### Soketler

Her oda tipinin soket yerleri sabittir. Çoğu oda aynı standart seti taşır, bazı odalar buna kendine özgü soketler ekler.

**Standart set:** 1 avize · 2 zemin plakası · 2 duvar (tablo ya da gargoyle, yani Göz) · 1 yaratık yuvası

| Oda | Standart setten farkı |
|---|---|
| Giriş Odası | Hiç soket yok |
| Şapel | Hiç soket yok |
| Koridor | Avize yok. +2 zırh nişi (Mimic Zırh), +1 Döner Duvar |
| Kütüphane | +2 raf arkası (kitap yağmuru, gizli geçit) |
| Yemek Salonu | 2 avize (en büyük tuzak odası) |
| Balo Salonu | +4 ayna soketi (ayna kırma tuzağı) |
| Kripta ↓ | Avize yok. +3 tabut (yaratık çıkışı) |
| Şarap Mahzeni ↓ | +2 fıçı (yuvarlanan fıçı tuzağı) |
| Portre Galerisi | 6 duvar soketi (en çok Göz) |

### Loot

Her oda temasına uygun loot getirir. Oyuncular objective odasına koşmak yerine odalarda vakit harcar.

| Tür | Ne işe yarar | Gerilim |
|---|---|---|
| Hazine | Şatodan çıkarılırsa ya da Kapıcı'da bankalanırsa bireysel puan verir. Kapıcı'da harcanabilir de | Ağır hazine iki elle taşınır, çelmeyle düşer. Ölünce yere düşer, başkası kapar |
| Ekipman | Bkz. İnsanlar ve ekipman | Hayatta kalmak için şart, ama envanter slotu sınırlı |
| Bilgi | Kat planı sayfası: objective odasının hangi kopyada olduğunu, odaların yerini ya da Kapıcı'nın odasını gösterir. Şato her round değiştiği için sadece o round geçerlidir | Paylaşırsan herkes kazanır, saklarsan sen |

- **Derinlik değer artırır:** Hazinenin değeri girişe olan mesafeyle yükselir.
- **Objective yine önemli:** Objective başarısız olursa hazine puanının sadece yarısı sayılır.
- **Tavan:** Toplam loot puanı objective teslim bonusunu geçmemeli.

| Oda | Hazine | Ekipman ve diğer |
|---|---|---|
| Giriş Odası | — | Başlangıç kiti sandığı |
| Yatak Odası | Drakula'nın mücevherleri (en yüksek değer) | — |
| Şapel | — | Kutsal su (sınırlı), haç |
| Koridor | Az | Tebeşir, fener yağı, kibrit, bilye torbası |
| Kripta ↓ | Mezar yüzükleri, altın sikke | Kazık, levye |
| Şarap Mahzeni ↓ | Eski şarap şişesi (kırılgan) | Sarımsak örgüsü, fener yağı, un torbası, levye |
| Balo Salonu | Mücevher, balo maskesi | El aynası (taşınabilir ayna), bilye torbası |
| Kütüphane | Nadir kitaplar | Kat planı sayfası, Drakula'nın Günlüğü (nadir), simya notu |
| Yemek Salonu | Gümüş çatal bıçak, gümüş şamdan (ağır) | Sarımsak, yemek zili, un torbası |
| Portre Galerisi | Küçük tablolar | Örtü bezi (Gözleri kapatmak için) |
| Gelin Odası | Mücevher kutusu | Anahtar |
| Simya Laboratuvarı | Simya altını | İksirler, flaş tozu (nadir) |

**Nadirlik:** Her eşya üç kademeden birindedir. *Yaygın* eşya her odada çıkabilir (fener yağı, kibrit, tebeşir). *Oda eşyası* sadece kendi oda tipinde çıkar (tablodakiler). *Nadir* eşyanın çıkma şansı girişten uzaklaştıkça artar. Güçlü eşyalar başlangıçta hiç yoktur; güç risk alarak kazanılır.

### Ekonomi ve Kapıcı

**Sorun:** Benzer oyunlarda para havuzu round'lar boyunca birikir ve insanlar giderek güçlenir. Bizde herkes sırayla Overlord olduğu için bu, ilk Overlord'un son Overlord'dan daha kolay kazanması demek olurdu.

**Çözüm:** Para ve eşya round'dan round'a taşınmaz, sadece puan taşınır ve puanla hiçbir şey alınmaz. Her round herkes aynı başlangıç kitiyle, Overlord da aynı Gold'la başlar. Benzer oyunlardaki "topla, güçlen, derine in" döngüsü tek bir round'un içinde yaşanır: Kapıcı sayesinde.

**Kapıcı**, şatonun açgözlü yaşlı uşağıdır. Hazine karşılığında eşya satar.

- **Yer:** Üretici Kapıcı'yı her round rastgele bir serbest odaya koyar. Yatak Odası, Şapel, objective odası ve Giriş'e bitişik odalar hariçtir. İnsanlar onu şatoyu gezerek ya da kat planı sayfasıyla bulur. Overlord yerini kurulumda görür.
- **Bankala ya da harca:** Kapıcı'ya getirilen hazine ya bankalanır ya da harcanır. Bankalanan hazine puana yazılır, artık çalınamaz ve çelmeyle düşmez (objective başarısız olursa yine yarısı sayılır). Harcanan hazine puan olmaktan çıkar. Güç ile puan arasında gerçek bir takas oluşur: çok harcayan daha kolay hayatta kalır ama puanı düşük kalır.
- **Stok:** Her round rastgele 3–4 eşya. Stok sınırlı ve herkese ortaktır; bir eşyayı ilk alan kapar. Overlord stoğu kurulumda görür ve tuzaklarını buna göre kurar.
- **Kapıcı'nın odası:** Bu odadaki soketler kapalıdır, Overlord buraya tuzak ya da yaratık koyamaz. Ama av sırasında Overlord'un kendisi oraya gelebilir; alışveriş yapanı beklemek meşru bir avdır.
- **Gece Yarısı:** İlk çanla Kapıcı kepenkleri indirir. Son 3 dakikada kimse güçlenemez ve bankalayamaz; hazine ancak şatodan çıkarılarak puana döner.

| Kapıcı stoğu örnekleri | Not |
|---|---|
| Tam yağlı yedek fener | Ucuz |
| Kutsal su | Orta |
| Kat planı sayfası | Orta |
| Flaş tozu | Pahalı |
| Gümüş Kazık | Round'da en fazla 1 adet, çok pahalı. Isırık anında kullanılırsa ısırığı iptal eder ve Overlord'u 10 sn fiziksel formdan atar |

Kesin fiyatlar playtest ile belirlenecek. Kural: en pahalı eşya, girişe yakın odalardaki tek bir hazineyle alınamamalı.

**Hesap ilerlemesi** (seanslar arası) güç değil çeşitlilik açar. Yeni eşyalar mevcutların sidegrade'idir ve aynı fiyat bandında durur. Lobide herkes aynı havuzdan çeker. Seans içinde oyuncuların şatoyu ve hileleri öğrenmesi iki tarafa da eşit işler; bu bir dengesizlik sayılmaz.

## Av fazı: Overlord

Overlord av boyunca görünmez gezer, Gözler'le oyuncuları bulur, fizikle oynar, konuşur ve cooldown'lu ability'lerini kullanır. Av Yatak Odası'nda başlar. Av sırasında Gold kullanılmaz, tek kaynak cooldown'lardır.

### Görünmez gezinti

- Birinci şahıs **sis formu**. Duvarlardan geçer, insanlardan biraz hızlıdır.
- Haritada insanları göremez. Onları **Gözler** ile bulur: kurulumda yerleştirdiği portreler ve gargoyle'lar canlı görüntü verir, ayrıca bir Göz'e anında ışınlanabilir. İnsanlar Gözler'i kırabilir ya da örtebilir.
- **İnsanlar için ipuçları:** yakındayken mum alevleri ona doğru eğilir, hafif nefes buharı oluşur. **Aynalarda görünür.**

### Fizik etkileşimi (cooldown yok)

- Eşya itme, kaldırma, fırlatma, sürükleme, kapı sallama, sandalye devirme.
- Ağırlık sınırı: küçük eşyalar fırlatılır, büyük mobilya sadece yavaşça itilir.
- **Oyuncu itme** de cooldown'suzdur. Ama Overlord bir oyuncuya dokunduğunda 1 saniyeliğine silueti görünür. İtme bedava kalır ama konum ifşa eder.
- Overlord'un fizikle yaptığı etkileşimler şatonun kendiliğinden olan ortam olaylarıyla aynı görünür (bkz. Atmosfer).

### Ses

| Mod | Nasıl duyulur | Bedeli |
|---|---|---|
| Fısıltı (proximity) | Yakındaki oyuncunun kulağının dibinde | Konumunu ele verir |
| Yankı (global) | Tüm dungeon'da reverb'lü, derin | Konum vermez, daha az kişisel |

İki modda da ses otomatik filtrelenir ki Overlord'un sesi Drakula gibi dursun ve bir oyuncunun sesiyle karışmasın.

### Ability'ler (örnek liste)

Overlord kurulum fazında açtığı havuzdan 3–4 aktif ability seçer. İnsanlar havuzu bilir ama seçimi göremez; Overlord'un hangi güçleri aldığını av sırasında görerek öğrenirler. Cooldown'lar ilk değerlerdir.

| Ability | Menzil | Etki | Cooldown |
|---|---|---|---|
| Karanlık | Oda | Odadaki tüm mumları söndürür | ~30 sn |
| Kilitle | Uzak | Bir kapıyı 15 sn kilitler | ~25 sn |
| Sahte Ses | Uzak | Bir odada ayak sesi ya da kapı vuruşu | ~20 sn |
| Döner Duvar | Uzak | Bir duvar döner, grubu ayırır | ~60 sn |
| Yarasa Sürüsü | Uzak | Görüşü kapatan gürültülü sürü | ~45 sn |
| Yaratığa Gir | Uzak | Bir yaratığı FPS olarak kontrol eder | ~90 sn |
| Isırık | Yakın | Lanet zinciri (bkz. Lanet sistemi) | ~40 sn |
| Hipnoz | Yakın | Lanetli oyuncuyu kendine çeker | ~60 sn |
| Beden Ele Geçirme | Yakın | Lanetli oyuncuyu ~10 sn kontrol eder | ~120 sn |
| Taklitçi | Uzak | Bir oyuncunun mimic'ini yaratır | ~120 sn |
| Tezahür | — | Drakula 25 sn fiziksel olarak belirir | ~4 dk, Gece Yarısı'nda yarısı |

Tezahür'deki Drakula çok güçlüdür ama ışık, sarımsak, haç ve kazıkla kovulabilir. Ayrıca Gece Yarısı'ndan önce kullanılamaz.

**Ability açma:** Yeni ability'ler hesap ilerlemesiyle açılır. Oyuncular oynadıkça havuz büyür; bu hem oynamaya devam etmek için bir sebep, hem de oyunu taze tutan şey. Havuz büyüdükçe insanların Overlord'un seçimini tahmin etmesi de zorlaşır.

## Lanet sistemi ve yakın mesafe tehditleri

Overlord'un uzaktan kullandığı güçler avı korkutup hazırlar (bkz. Dehşet sistemi), yakından kullandıkları öldürür. Overlord'un odada olduğunu fark eden oyuncunun kaçması gerekir.

**Lanet zinciri:** Normal → (1. ısırık) → Lanetli → (2. ısırık) → Ölü / Hizmetkâr. Lanetli, Şapel'de Normal'e döner.

İlk ısırık oyuncuyu Lanetli yapar, ikinci ısırık öldürür ve hizmetkâra çevirir. Şapele ulaşan Lanetli temizlenebilir ama bu yolculuk bireysel yarışta vakit kaybettirir.

### Isırık

- Isırık için Overlord'un kısa bir an **fiziksel forma** geçmesi gerekir. Işık varken Overlord fiziksel forma geçemez, bu yüzden ışıktaki oyuncu ısırılamaz. Işık ısırığı değil, formu engeller. Sadece mum ve fener ışığı sayılır; pencereden giren ay ışığı fiziksel formu engellemez.
- **Dehşet'teki oyuncu tek ısırıkta ölür,** Lanetli aşaması atlanır (bkz. Dehşet sistemi).
- "Karanlık" ability'si ile Isırık en ölümcül kombo. Okunması da net: Overlord'dan şüphelendiğin bir odada mumlar sönerse, kaç.
- Lanetlinin aynada yansıması yoktur. "Neden aynaya bakmıyorsun?" paranoyası buradan gelir.

### Hipnoz

Lanetli oyuncunun kamerası yavaşça Overlord'a döner ve karakter ona doğru yürür. Fiziksel form gerektirmez, ışıkta da çalışır: Overlord ışıkta ısıramadığı Lanetliyi Hipnoz'la karanlığa çekebilir. Arkadaşları onu tokatlayarak ya da sürükleyerek kurtarabilir. Bireysel oyunda kurtarıp kurtarmamak da bir karar.

### Beden Ele Geçirme

- Sadece Lanetli oyunculara, yakın mesafede, ~10 saniye. Fiziksel form gerektirmez, ışıkta da çalışır.
- Overlord kurbanın hareketini ve elindeki eşyayı kontrol eder: objective'i çukura atar, arkadaşını iter.
- Kurbanın **sesi kesilir.** "Ahmet neden sustu?" sessizliği hem kanıt hem korku kaynağı.
- Kurban olanları ekranından izler ama hiçbir şey yapamaz.

## Dehşet sistemi

Overlord korkutarak avlanır: korkutulan oyuncu daha kolay bulunur ve daha kolay ölür. Dehşet puan getirmez, sadece Overlord'un güçlerini besler.

Her insanın gizli bir Dehşet seviyesi vardır: **Sakin → Tedirgin → Dehşet**. Bu bar hiçbir oyuncuya gösterilmez; insanlar onu sadece oyun içindeki belirtilerle hisseder. Mikrofon kullanılmaz. Oyuncular ve hizmetkârlar kimseyi korkutamaz; seviyeyi Overlord ve şato değiştirir. Şatonun odalarda rastgele olan doğaüstü olayları Dehşet'i en fazla bir seviye, Sakin'den Tedirgin'e çıkarabilir. Bir oyuncuyu Dehşet'e sadece Overlord taşıyabilir.

### Dolduran ve düşüren

| Dolduran | Düşüren |
|---|---|
| Yakınında kullanılan ability (Karanlık, Sahte Ses, Kilitle, Yarasa Sürüsü) | Mum ya da fener ışığı |
| Overlord'un fiziği: yakına düşen eşya, çarpan kapı | Yanında yaşayan başka bir insan |
| Kulağa fısıltı, dokunma ya da itme | Şapel |
| Aynada Overlord'u görmek, mimic, yaratık kovalaması | Uyaran olmadan geçen süre |

Karanlıkta ve yalnızken seviye daha hızlı dolar.

- **Aynı numara azalır:** Aynı tür uyaran tekrarlandıkça daha az korkutur. Overlord çeşitlilik yaratmak zorundadır.
- **Yığılan uyaranlar tek sayılır:** Aynı anda atılan 4 ability tek uyaran gibi işler. Korku aralıklı ve tırmanan uyaranlarla dolar. Bu kural "oyuncuyu görünce her şeyi bas" stratejisini bozar.
- **Korku söner:** Overlord uzaklaşınca seviye zamanla iner, sonraya saklanamaz.
- **Dehşet kısa sürer:** ~20 sn sonra Tedirgin'e düşer. Hazırlanan av zamanında hasat edilmelidir.

### Overlord'a kazandırdıkları

1. **Tek ısırık:** Dehşet'teki oyuncu tek ısırıkta ölür ve hizmetkâr olur. Sakin ve Tedirgin oyuncular için lanet zinciri aynen işler.
2. **Korkunun kokusu:** Overlord, Tedirgin ve Dehşet'teki oyuncuların kalp atışını duvarların arkasından duyar. Uzak güçler böylece avı hazırlamaya ve işaretlemeye yarar.
3. **Cooldown yenilemesi:** Bir oyuncu Dehşet'e her girdiğinde Overlord'un bütün cooldown'ları ~10 sn azalır. Overlord'un seçtiği ability'ler de gizli olduğundan insanlar cooldown sayıp "şu an güvendeyiz" diyemez.

### İnsanlar nasıl hisseder

| Seviye | Belirtiler |
|---|---|
| Sakin | Belirti yok |
| Tedirgin | Fener hafifçe titrer, nefes sesi duyulur |
| Dehşet | Eller titrer, taşınan eşya kayabilir, karakter arada istemsiz inler. Bu ses karakterin kendi sesidir, mikrofon değil; konumunu herkese ele verir |

Diğer oyuncular da bu belirtileri görür ve duyar. Feneri zangır zangır titreyen arkadaşının yanına gidip onu sakinleştirmek hedefin yanında durmak demektir; onu yem olarak bırakmak da bir seçenektir. Overlord'un "Biri ayna önündeyken onu korkut" görevi artık o oyuncunun Dehşet seviyesini yükseltmek demektir.

**Av döngüsü:** Bul (Gözler) → Hazırla (uzak güçler, fizik, fısıltı) → Zirve (Dehşet) → Hasat (Karanlık + Isırık) → kurban ölür ya da Şapel'e koşar → sıradaki av.

## Mimic'ler ve ses kaydı

Oyun maç boyunca oyuncuların proximity sesinden kısa klipler kaydeder. Overlord bu klipleri, yarattığı bir oyuncu kopyasının ağzından çalıp diğer oyuncuları kandırır.

### Ses kaydı

- Ses aktivitesi algılandığında 1–3 saniyelik klipler otomatik kesilir.
- Her oyuncu için son ~15 klip tutulur. Maç bitince hepsi silinir.
- Overlord mimic'i kontrol ederken o oyuncunun kliplerini bir **soundboard** üzerinden dinleyip seçer. Kontrol etmediği sırada AI rastgele klip çalar.
- Bağlamından kopmuş cümleler kendiliğinden komedi üretir.
- Lobide oyuncunun ses kaydına izin vermesi gerekir.

### Mimic türleri

| Tür | Nasıl oluşur | Nasıl anlaşılır |
|---|---|---|
| Ölü Taklitçi | Ölen oyuncunun bedeninden bir kopya | Aynada yansıması yok, eşya tutuşu tuhaf |
| Canlı Taklitçi | Yaşayan bir oyuncunun kopyası; ortalıkta iki Ahmet olur. Pahalı, uzun cooldown, Gece Yarısı'nda ucuzlar | Ayna, tuhaf eşya tutuşu, kutsal su |

## Atmosfer ve belirsizlik

Şato kendi kendine yaşar, bu yüzden oyuncu bir olayın Overlord'dan mı yoksa şatodan mı geldiğini asla bilemez. Gerilimi üreten şey o karar anı: kaçarsan vakit kaybedersin, kalırsan ölebilirsin.

### Ortam olayları

- Overlord'dan bağımsız, rastgele aralıklarla: mumlar titrer ya da söner, kitap raftan düşer, kapı gıcırdar, sandalye kayar.
- Overlord'un fizik etkileşimleri ortam olaylarıyla **aynı görünür ve aynı sesi çıkarır.**
- Sıklığı saat ilerledikçe artar, Gece Yarısı'nda zirve yapar.
- Her odada rastgele doğaüstü olaylar gerçekleşebilir. Bu olaylar Dehşet'i Sakin'den Tedirgin'e çıkarabilir ama daha yukarı taşıyamaz (bkz. Dehşet sistemi).

### Gerilim efektleri (fizik komedisi)

- **Titreyen fener:** Yağ azalıyor olabilir, bir ortam olayı olabilir ya da Overlord yakında olabilir.
- **Eşya düşürme ve kayma:** Taşınan eşyalar fizikle hareket eder. Ani bir sarsıntıda ya da itilince düşer.
- **Ragdoll:** İtilen, tuzağa yakalanan, merdivenden düşen karakterler fizikle savrulur.

Korku ekonomisi için mikrofon ya da çığlık algılama kullanılmaz. Mikrofon yalnızca mumlarla etkileşimde kullanılır (aşağıda).

### Aynalar

Aynalar otomatik döşemeyle rastgele yerleşir ve gerçeği gösterir:

- Görünmez Overlord aynada görünür.
- Lanetli oyuncunun yansıması yoktur.
- Mimic'in yansıması yoktur.

### Mikrofon ve mumlar (geliştirme sırasında eklenecek)

Mumlar oyuncunun mikrofonuna fiziksel olarak tepki verir: konuşan oyuncunun yanındaki alev titrer ve itilir, mikrofona üflenirse mum söner.

- **Üfleyerek söndürme:** Saklanmak için işe yarar ama karanlık Isırık'a kapı açar. Bir arkadaşının mumunu üfleyip onu karanlıkta bırakmak da bir ihanet hamlesi olur.
- **Belirsizliği büyütür:** Titreyen bir alevin nedeni artık üç tane: şato, Overlord ya da konuşan bir oyuncu.
- **Overlord için ipucu:** Gözler'den bakan Overlord, titreyen mumlardan bir odada birinin konuştuğunu anlayabilir. Sessiz kalmak bir strateji olur ama zorunlu değildir.
- Bu bir korku ölçeri değildir, sadece fiziksel bir etkileşimdir.

## İnsanlar ve ekipman

Her eşyanın bir yardım, bir de ihanet kullanımı vardır. Doğrudan PvP öldürme yoktur: sabotaj var, cinayet yok, yoksa oyun co-op hissini kaybeder.

**Envanter:** 2 el + 3 cep. Fener kemere takılabilir: eller boşalır ama ışık daralır. Taşınabilir mum yoktur; şatodaki mumlar yerinde kalır, kibritle yakılır.

### Başlangıç kiti (kör draft)

- **Herkese sabit:** Fener (yarım yağ) + kibrit kutusu (3 kibrit).
- **Seçmeli, 3 Hazırlık Puanı:** Giriş Odası'ndaki sandıktan.
  - 1 puan: Tebeşir, Sarımsak, Un torbası, Fener yağı
  - 2 puan: Kutsal su (1 doz), El aynası
- İnsanlar kitini Overlord kurulum yaparken aynı anda seçer. Overlord ability'lerini gizli seçer, insanlar da kitlerini; iki taraf da birbirine karşı eşit derecede kördür.
- Güçlü eşyalar (haç, kazık, flaş tozu, Günlük) başlangıç kitinde yoktur, sadece odalardan ya da Kapıcı'dan gelir.

### Eşya havuzu

| Rol | Eşya | Yardım | İhanet |
|---|---|---|---|
| Işık | Fener | Yanındayken Overlord fiziksel forma geçemez, yani ısıramaz. Yağı biter | Arkadaşının gözünü kamaştır, onu karanlıkta bırak |
| Işık | Kibrit | Şatodaki sabit mumları yakar | Son kibriti kendine sakla |
| Işık | Fener yağı | Feneri doldurur | — |
| Işık | Flaş tozu (nadir) | Odayı 1 sn kör eden ışık; o an yapılan ısırığı iptal eder | Herkesi kör et, kaç |
| Tespit | El aynası | Overlord'u, Lanetlileri ve mimic'leri gösterir | — |
| Tespit | Un torbası | Yere serpilir; görünmez Overlord üstünden geçerse ayak izi çıkar | Arkadaşının ayağına bulaştır, Overlord onun izini takip etsin |
| Tespit | Bilye torbası | Yere dökülür; görünmez Overlord üstünden geçerse bilyeler ses çıkarır | Kaçış yoluna dök, arkadaşın kaysın |
| Tespit | Tebeşir | Yol işaretler | Yanlış ok çizer |
| Koruma | Kutsal su | Laneti temizler, mimic'i ifşa eder | Boşa harcatır; şapeldeki son suyu sen al |
| Koruma | Sarımsak | Yaratıkları bir bölgeden uzak tutar | Bölgeyi sadece kendin için kur |
| Koruma | Haç | Yaratıkları ve Tezahür'ü iter. İki elle tutulur, eşya taşınamaz | Korumayı son anda bırak |
| Koruma | Kazık | Tezahür'deki Drakula'yı bir kez sersemletir | — |
| Koruma | Gümüş Kazık (sadece Kapıcı) | Isırığı iptal eder, Overlord'u 10 sn fiziksel formdan atar | — |
| Fayda | Anahtar | Kilitli kapıları açar | Kapıyı arkadaşının arkasından kilitle |
| Fayda | Levye | Kilitli kapıyı ya da tabutu zorla açar, çok gürültülüdür | Dolap kapısını sıkıştır, arkadaşını içeride kilitle |
| Fayda | Zil | Yaratıkları bir noktaya çeker | Yaratıkları arkadaşının üstüne çeker |
| Fayda | Örtü bezi | Portreyi ya da Göz'ü örter | — |
| Bilgi | Kat planı sayfası | Objective'in kopyasını, oda yerlerini ya da Kapıcı'yı gösterir | Kendine sakla |
| Bilgi | Simya notu | Bir iksir renginin etkisini açıklar | Yanlış söyle |
| Bilgi | Drakula'nın Günlüğü (nadir) | Overlord'un seçtiği ability'lerden birini ifşa eder | Öğrendiğini kendine sakla |

**Çelme / itme** her oyuncunun temel hareketidir: objective taşıyanın elinden eşyayı düşürür, sen kaparsın.

**Şapel** güvenli odadır: laneti temizlemenin tek yeri ve kutsal suyun kaynağı. Miktar sınırlı olduğu için çekişme noktası da olur.

### Saklanma

Dolap, tabut ve yatak altı saklanma noktalarıdır. Yerlerini otomatik döşeme belirler.

- İçerideyken görüş sadece bir aralıktan olur ve Gözler seni göremez.
- Overlord kapağı fizikle açabilir (cooldown yok), ama bunun için yanına gelmesi gerekir. Saklanmak ona karşı bir kumardır.
- **İhanet:** Arkadaşının saklandığı dolabın önüne ağır bir eşya itersen onu içeride kilitlersin.
- **Tabut:** İçinden hazine, bir yaratık ya da boşluk çıkabilir.
- **Mahzende:** Saklananın nefes buharı kapaktan sızar.

### İksirler

Simya Laboratuvarı'ndan çıkar. Renk ile etki arasındaki eşleşme her maç seed'le değişir, yani içmeden ne olduğu bilinmez. Kütüphanedeki simya notu bir eşleşmeyi açıklar. İksir içilebilir ya da bir arkadaşa fırlatılabilir.

| İksir | Etki |
|---|---|
| Hız | 10 sn hızlı koşma |
| Gece Görüşü | Karanlıkta görme, ama ışık gözü kamaştırır |
| Sessiz Adım | Ayak sesi çıkmaz |
| Kusma | Gürültülü, yaratıkları çeker |
| Yansımasızlık | Aynada yansıman olmaz, herkes seni Lanetli sanır |
| Drakula Sesi | Sesin Overlord filtresine girer, herkes seni Overlord sanır |

## Objective'ler

Her round'da bir ana objective rastgele seçilir ve herkes onu görür. Ayrıca her oyuncuya, Overlord dahil, sadece kendisinin bildiği gizli görevler verilir.

### Ana objective havuzu

Her objective hem insanların oynayışını hem de Overlord'un tasarımını değiştirir. Teslim eden kişi büyük bir bonus alır.

| Objective | Oda | Mekanik | Ürettiği an |
|---|---|---|---|
| Kalbi Çal | Yatak Odası | Kavanozdaki kalp atar, ses yayar, yaratıkları çeker; tek kişi taşıyabilir. Kalp Overlord'un av başlangıcı olan odadan çalınır | Kimse taşımak istemez ama herkes teslim etmek ister |
| Tabutu Çıkar | Kripta ↓ | 2+ kişiyle fiziksel taşıma, yeraltından merdivenle yukarı, dar kapılar | Fizik kaosu; taşıyıcılardan biri işi bırakıp kaçabilir |
| Kara Ayin | Balo Salonu | 4 mumu yaklaşık aynı anda yakmak | Grup bölünmek zorunda, yalnızlık korkusu |
| Gerçek Portre | Portre Galerisi | 20 portreden biri gerçek; yanlışı alan alarmı çalar | Mimic paranoyası |
| Gelini Kurtar | Gelin Odası | NPC gelin escort edilir, kendi kafasına gezer, Overlord onu ele geçirebilir | "Gelin neden bize doğru koşuyor?" |
| Şarap Mahzeni | Şarap Mahzeni ↓ | Kırılgan şişelerle kota doldurmak | Düşürülen, çalmaya kalkılan şişeler |

### Gizli yan görevler

> **⚠ ASKIDA (2026-11-07):** Gizli görev sistemi şimdilik askıya alındı. Bu bölümdeki tasarım ve sonradan denenen yönler tatmin edici bulunmadı. Playtest'lerde bireysel hedef eksikliği hissedilirse yeniden ele alınacak. Aşağıdaki içerik referans olarak duruyor; geçerli tasarım değildir. Tek kesin karar: **Kan Paktı** (bir insanın Overlord'la gizli anlaşması) sadece 5–6 kişilik oyunlarda opsiyon olacak, 3–4 kişide olmayacak.

Gizli görev, ana gameplay'den ayrı bir iş değildir. Oyuncunun zaten yaptığı işi **nasıl** yaptığını değiştirir. Overlord kendi gizli görevini objective'le birlikte (0. Kontrat), kurulumdan önce öğrenir. İnsanlar avdan hemen önce öğrenir. Round sonunda hepsi ifşa edilir; bu, round sonunun en komik anı olmalı.

#### Tasarım kuralları

1. **Yol üstünde:** Görev oyuncuyu zaten gideceği odalara ve dokunacağı eşyalara bağlar. Ana rotadan en fazla 1 oda sapma ve toplam 30–60 sn efor ister.
2. **Gerçek şatodan üretilir:** Görevler otomatik döşemeden sonra, bitmiş şatoya bakılarak üretilir. Sadece gerçekten var olan oda ve eşyalardan görev çıkar; imkânsız görev olmaz.
3. **Durdurmaz, garip gösterir:** Görev oyuncuyu şüpheli göstermeli ("Bu adam neden şamdanla koşuyor?"). Şüphe ve komedi buradan doğar.
4. **Objective'den az değerli:** Kimse objective'i bırakıp görev kovalamamalı, ama yakın skorlarda seansı çevirebilmeli.

#### Format

- Avdan hemen önce mühürlü bir mektup gelir. *(Karar bekliyor: 2 görev çekip 8 sn içinde 1 seçmek mi, yoksa tek görev mi?)*
- Ekranda tek satır yazı. Waypoint ya da ok yok.
- Görev tamamlanınca sadece o oyuncu duyar: mühür kırılma sesi.

#### Görev aileleri

| Aile | Mantık | Örnekler | Risk |
|---|---|---|---|
| **Kaçakçı** | Bir eşyayı A'dan B'ye taşı | Yemek Salonu'ndan gümüş şamdanı şatodan kaçır · Mahzen'den bir şarap şişesini kırmadan Şapel'e götür · Drakula'nın Günlüğü'nü bul ve oku | Ağır ya da kırılgan eşya yavaşlatır, fizik komedisi |
| **Cüretkâr** | Bir sistemi bilerek riske at | Kripta'da fenersiz 20 sn kal · Overlord aynı odadayken dolapta saklan ve hayatta kal · Fener yakmadan hayatta kal | Overlord'un yakın mesafe gücüne kendini açarsın |
| **Ritüel** | Zaman ve yer koşulu | Gece Yarısı çanı çaldığında Şapel'de ol · Yemek Salonu'ndaki bütün mumları yak · Şatodan son çıkan kişi ol | Belli bir anda belli bir yerde olursun, tahmin edilebilir hale gelirsin |
| **Kuyu kazıcı** | Başka bir oyuncuya karşı (round başına en fazla 1 kişiye) | X'in taşıdığı bir eşyayı al · Birine Simya'dan bir iksir içir · Birini 10 sn dolaba kilitle · Tabutu en az bir kez düşür | Yakalanırsan sana karşı ittifak kurulur |

**Çakışan görevler:** Sistem bazen iki oyuncuya aynı eşyayı verir. Biri "şişeyi Şapel'e götür", diğeri "şişeyi kır" görevini alır. Kuyu kazma tasarlanmadan, kendiliğinden doğar.

#### Overlord'un gizli görevleri

Kazanmanın tek yolu öldürmek olmasın ve her turda farklı bir av tarzı çıksın diye:

- İlk ısırığını Balo Salonu'nda yap.
- Biri ayna önündeyken onu korkut.
- Tabutu taşıyan birini öldür.
- Bir mimic'le bir oyuncuyu tuzağa çek.
- Beden ele geçirip bir insana diğerini ittir.

**Fısıltı** *(öneri, karar bekliyor)*: Overlord rastgele bir insanın gizli görevini öğrenir. Yankılı sesle *"Şamdanı mı arıyorsun?"* demek ucuz ama çok etkili bir korku anı.

#### Hizmetkâr görevleri *(öneri, karar bekliyor)*

Oyuncu ölünce eski görevi yanar, yerine bir hizmetkâr görevi gelir. Böylece ölen oyuncu oyunda kalır:

- Yaşayan birinin elindeki eşyayı düşürt.
- Bir insanı tuzağa çek.

#### Maç sonu ifşa

Her oyuncunun görevi sırayla açıklanır. Görevin tamamlandığı anın otomatik çekilmiş bir fotoğrafı da gösterilir.

#### Bilerek dışarıda bırakılanlar

- **Mikrofon gerektiren görevler:** Oyuncular mikrofonu kapatıp meta yapar (mic tabanlı korku ekonomisi zaten iptal).
- **"X'i öldür" görevleri:** Tek bir kişiyi hedefler, griefing'e döner.
- **Objective'i doğrudan sabote eden hain:** Oyunu social deduction'a çevirir. Olacaksa ayrı mod olur.
- **Uzun görev zincirleri:** Akışı en çok bozan şey.

## Ölüm ve Hizmetkâr

Ölen insan izleyiciye dönüşmez, Overlord'un hizmetkârı olur. Oyun bireysel olduğu için arkadaşlarına karşı çalışması da mantıklıdır.

- **Amacı:** Lorduna gizlice yardım etmek. İnsanları korkutamaz, Dehşet'i yükseltmez.
- **Formu:** Yarasa ya da kambur bir uşak. Görünürdür.
- **Yapabildikleri:** Kapı açar, eşya saklar, tebeşir oklarını bozar, kendi sesiyle konuşup arkadaşlarını yanlış yöne çeker.
- **Yapamadıkları:** Öldüremez, objective taşıyamaz.
- **Ses:** Hizmetkârın sesine hafif bir filtre eklenir ki mimic sistemiyle karışmasın.

Hizmetkârın nasıl çalışacağı playtest'te netleşecek. Her ölen insanın otomatik hizmetkâr olması yerine hizmetkâr, bir ability'den gelen bir güç de olabilir.

### Hizmetkâr puanı

- Overlord kazanırsa hizmetkârlar küçük bir pay alır.
- Overlord'a yardım ederek de puan kazanır (örnek: bir oyuncuyu tuzağa çekmek).
- **Denge kuralı:** Bir hizmetkârın alabileceği en yüksek puan, hayatta kalan sıradan bir oyuncunun puanından her zaman düşük olmalı. Yoksa oyuncular bilerek ölüp Overlord tarafına geçer.

## Gece Yarısı ve çan saati

Oyun içi saat 21:00'de başlar ve her saat başı çan çalar. Oyuncular ekrana bakmadan zamanı bilir; çanlar sıklaştıkça sürenin azaldığını ve Overlord'un güçlendiğini anlar.

1. **21:00, 22:00, 23:00:** Çan her saat başı çalar. Ortam olayları her saat biraz daha sıklaşır.
2. **24:00, Gece Yarısı:** Çan 12 kez çalar.
  - Overlord'un cooldown'ları yarıya iner.
  - Tezahür açılır.
  - Canlı Taklitçi ucuzlar.
  - Ortam olayları zirve yapar.

3. **Gece Yarısı'ndan 3 dk sonra (gerçek süre):** Köprü kalkar, şato kapanır. İçeride kalan herkes ölür ve hizmetkâr olur.

Son üç dakika asıl karar anıdır: kalbi alıp kaçmak mı, yoksa son gizli görevi yapmak mı?

## Puanlama ve tek kazanan

Seans sonunda en yüksek bireysel puana sahip oyuncu kazanır. Herkes eşit sayıda Overlord olduğu için Overlord ile insan arasındaki denge farkı seans sonunda büyük ölçüde nötrleşir.

| Kaynak | Kim alır | Puan |
|---|---|---|
| Ana objective başarılı | Hayatta kaçan her insan | Taban puan (yüksek) |
| Ana objective başarılı | Ölen insanlar | Daha düşük taban puan |
| Objective'i teslim etmek | Teslim eden (tabutta taşıyıcılar arasında bölünür) | Büyük bonus |
| Gizli görev | Görevi tamamlayan herkes | Orta |
| Öldürülen her insan | Overlord | Orta |
| Başarısız objective | Overlord | Yüksek |
| Overlord kazanırsa pay | Hizmetkârlar | Düşük |
| Overlord'a yardım | Hizmetkârlar | Düşük |
| Şatodan çıkarılan ya da Kapıcı'da bankalanan hazine | Hazineyi taşıyıp kaçan ya da bankalayan | Hazinenin değeri kadar (objective başarısızsa yarısı). Kapıcı'da harcanan hazine puan vermez |

Taban puan insanların işbirliği yapması için bir neden bırakır; teslim bonusu ve gizli görevler ise birbirlerinin kuyusunu kazmaları için. Kesin rakamlar playtest ile belirlenecek.

## MVP, teknik notlar ve açık sorular

İlk oynanabilir sürüm çekirdek döngüyü test etmeli: şato üretimi ve tuzak kurulumu, görünmez Overlord, yakın mesafe tehdidi ve bireysel puan.

### MVP kapsamı

- 1 kat + yeraltı, 8 oda tipi (Giriş Odası, Yatak Odası, Şapel, Kripta, Şarap Mahzeni, Koridor, Kütüphane, Yemek Salonu), oda başına 3 layout şablonu ve otomatik döşeme
- Şato üreticisi (4 kapılı grid, oda seti, karmaşıklık kuralları), sadece tuzak ve yaratık için Gold havuzu, sabit soket setleri, saklanma, oda bazlı loot, başlangıç kiti ve Kapıcı
- 3 yaratık: Ghoul (kovalar), Mimic Zırh (pusu), Yarasa sürüsü (gürültü)
- 2 objective: Kalbi Çal, Tabutu Çıkar
- Görünmez Overlord, Gözler, fizik etkileşimi, iki ses modu
- 6 ability: Karanlık, Kilitle, Sahte Ses, Yaratığa Gir, Isırık, Hipnoz
- Ortam olayları, aynalar, çan saati
- Hizmetkâr ve temel puanlama

**Sonraki aşama:** Tezahür, Beden Ele Geçirme, ses kaydı ve mimic'ler, mikrofonla mum etkileşimi, gizli görevlerin tamamı, diğer objective'ler ve odaları (Balo Salonu, Portre Galerisi, Gelin Odası), Simya Laboratuvarı ve iksirler, Kule Merdiveni ile çok katlı şato.

### Teknik notlar

- Ses kaydı için ham ses verisine erişebilen bir voice chat sistemi gerekir (örnek: Unity'de Dissonance, Steam Voice).
- Overlord'un fizik etkileşimleri ve ragdoll'lar ağ üzerinden senkronize edilmeli; friend-slop oyunlarda küçük desync'ler kabul edilebilir ama taşınan objective sunucu otoritesinde olmalı.
- Şato üretimi ve otomatik döşeme seed tabanlı olmalı: tek bir seed tüm istemcilerde aynı şatoyu ve aynı odaları üretir.

### Açık sorular

- Overlord kurulum yaparken (~2 dk) insanlar ne yapacak? Ekipman seçimi yeterli mi, yoksa bir meyhane/hazırlık alanı mı olmalı?
- Overlord şatoyu ilk kez kurulumda görüyor: ~2 dakika hem haritayı okumaya hem tuzak kurmaya yetiyor mu?
- Üretici ne kadar sıkışık olmalı: grid ne kadar dar, kapıların ne kadarı duvara çevrilmeli? Playtest'le ayarlanacak.
- Yaratıklar ve tuzaklar doğrudan öldürür mü, yoksa sadece hasar verip Lanet zincirine mi bağlanır?
- Hizmetkâr şapelde geri kurtarılabilir mi?
- Overlord'un kurulum ekranı hangi kamerada olacak: yukarıdan harita masası mı, birinci şahıs mı?
- Oyuncu sayısı aralığı kaç olacak (örnek: 3–6)?
- Kripta ve Mahzen'in merdiven ağzı tek kapılı mı olsun, 2 kapılı mı?
- Ability havuzu ayrıca tasarlanacak: başlangıç havuzunda hangileri olacak, hangileri ilerlemeyle açılacak?
- Hizmetkâr her ölümde otomatik mi olsun, yoksa bir ability'den mi gelsin? Playtest'te denenecek.
- Kapıcı fiyatları ve hazine değerleri: harcamak ile bankalamak arasındaki takas gerçekten zor bir karar olmalı. Playtest'le ayarlanacak.
- Hizmetkârlar Kapıcı'yla etkileşebilir mi (örnek: stoktaki eşyayı insanlardan önce kapıp saklamak)?
