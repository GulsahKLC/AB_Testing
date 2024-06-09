# AB_Testing
![download](https://github.com/GulsahKLC/AB_Testing/assets/100443116/8988d54c-a5d1-48ac-b22f-21d8b0cc4f70)

##### AB testleri veri bilimi alanında en çok kullanılan yöntemlerden birisidir. AB den kasıt iki grubun iki özelliğin birbiri ile karşılaştırılmasıdır. A bir grubu B bir grubu temsil etsin. Bu iki grup arasında farklılık olup olmadığı konusunda incelemeler yaptığımız kıyaslama işlemidir. Bir sitenin tasarımı yapılmak istendiği zaman hangi tasarımın kullanıcılar tarafından daha dikkat çekici olduğu, ilaç şirketleri için hangi ilacın daha faydalı olduğu ve piyasaya sürülmesi gerektiğine, yeni tasarlanmış bir ara yüzün eski arayüz ile karşılaştırılıp kullanılmasına, buna göre yapılacak maliyetlerin harcamaların planlanması gibi arkasında uygulanacak işlemler için bir planlama arenasıdır AB Testleri.

##### Kadıköy ile Bakırköy şubeleri olan bir firmanın bütçe problemleri için şirketini kapatmak istediğini düşünelim. 65,000 Tl ile 55,000 tl net karı olan bir şirketimiz olsun bu şirketler için bu ortalama sağlam bir ortalama mı ? Ortalamalar kıyaslanıyor ama bu sağlıklımıdır? Sağlıklı olduğunu varsayalım. Bakırköyü kapatıyoruz diyebilir miyiz ? Bakırköyde o periyotta tadilat olabilir mevsimsel sıkıntılar olabilir bu durum şans eseri mi yoksa gerçekten de böyle mi olduğu araştırılmalı. Tesadüfi mi gerçekleşmiş yoksa gerçekten bu durum böyle mi test edilmeli. Bu fark şansa yer bırakmayacak kadar kesin bir fark mıdır? Bu örnek aslında bir örneklemdir belli bir hatayı içinde barındırır. istatistiksel hipotezler kurup test etmeliyiz.

### Senaryo
##### Bir fast food zinciri menüsüne yeni bir ürün eklemeyi planlıyor. Ancak üç olası seçenek arasında hâlâ kararsızlar. Yeni ürünü tanıtmak için pazarlama kampanyası yapıp hangi promosyonun satışlar üzerinde en büyük etkiye sahip olduğunu belirlemek için yeni ürün bölgelerdeki lokasyonlarda tanıtılmaktadır:

#### Rastgele seçilmiş birkaç pazara, her lokasyonda farklı bir promosyon uygulanmakta ve haftalık satışlar yapılmaktadır.
![download (1)](https://github.com/GulsahKLC/AB_Testing/assets/100443116/8726a54e-bd8b-4c90-91e4-03dd29c145d5)

### Amaç
##### A/B testi sonuçlarını değerlendirin ve hangi pazarlama stratejisinin en iyi sonuç verdiğine karar verin

### Değişkenler
MarketID: pazarın benzersiz tanımlayıcısı
MarketSize: satışlara göre pazar alanının büyüklüğü
LocationID: mağaza konumu
AgeOfStore: mağazanın yıl cinsinden yaşı
Promosyon: Test edilen promosyonlar
week: haftalar
SalesInThousands: belirli bir LocationID, Promosyon ve hafta için satış tutarı

### 1. Hipotezleri Kur
#####  H0 hipotezi yokluk hipotezidir. Yani referans alacağımız ve buna göre yorum yapacağımız alandır. H1 i kabul ederim gibi bir yorum yapılamaz. H0 red veya kabul edilir. Sebebi ise; H0 ı red ettiğimiz zaman yapacak olduğumuz hata miktarını biliyor oluruz. H1 hakkında matematiksel bir hata metriği yoktur. alfa = 0,05 değeri bizim referans noktamızdır ve bu zemine göre t, z değerleri hesaplanmıştır.Red etme yada red edememe durumunda H0 referans alırız.
### 2. Varsayım Kontrolü
##### Normallik Varsayımı (Shapiro–Wilk test)
.H0: Normal dağılım varsayımı sağlanmaktadır. (shapiro testi normal dağılıp dağılmadığını test eder.)
.H1: Normal dağılım varsayımı sağlanmamaktadır.

### Varyans Homojenliği (Levene test)
### 3. Hipotezin Uygulanması
Varsayımlar sağlanıyorsa bağımsız iki örneklem t testi
Varsayımlar sağlanmıyorsa mannwhitneyu testi ya da değişken sayısına göre uygun testin seçilmesi
### 4. p-value değerine göre sonuçları yorumla
#### p value kabul edilebilir hata miktarıdır. alfa=0,05 ve p value değeri karşılaştırılarak hipotez testi yorumlanır.
Not:

#### Normallik sağlanmıyorsa direkt 2 numara. Varyans homojenliği sağlanmıyorsa 1 numaraya arguman girilir.
#### Normallik incelemesi öncesi aykırı değer incelemesi ve düzeltmesi yapmak faydalı olabilir.
#### İlk adımdan başlayalım ##### Hipotezleri Kur
H0: M1 = M2 = M3 -> Promosyonların satışları arasında fark yoktur.
H1: M1 != M2 != M3 -> promosyon satışları arasında fark vardır.En birisi arasında fark vardır.
#### Normallik Varsayımı
#### . H0: Normal dağılım varsayımı sağlanmaktadır. (shapiro testi normal dağılıp dağılmadığını test eder.)
#### . H1: Normal dağılım varsayımı sağlanmamaktadır.
##### p-value < ise 0.05'ten H0 RED. kararı idi. Görüyoruz ki test istatistiğinin değeri 0,7644 p değeri 0,000 dolayısı ile p_değeri < 0,05 olduğundan H0 red edilir. Normallik varsayımı sağlanmadığı için Parametrik olmayan Testlerden yolumuza devam edicez. Yinede varyansların homojenliğini de kontrol edelim.

#### Varyans Homojenligi Varsayımı
#####  levene testi ile varyansların homojenliği test edilir.

#### ANOVA Testi
##### Normallik varsayımı karşılanmadığı durumda Parametrik olmayan testler kullanılır. Birden fazla grubu kıyaslayarak gruplar arasında bir farklılık olup olmadığı konusunda bilgi verir.

##### Parametrik olmayan testlerden Kruskal Wallis testi ile uygula. Değişken sayısı 3 ve üstünde ise normallik varsayımı sınanması sonucu normal dağılıma uymadığı için Kruskal Wallis testi uygulanır. 2 değişken için Mann-Whitney U testi uygulanır.

##### p değeri = 0,000 < 0.05 H0 red edilir. Promosyonların satışları arasında fark vardır.
