# Keras-Cifar100

İlk olarak load_data metodu ile veri setini indirdim, gerekli değişkenlerin içerlerine attım. Train ve test 
klasörümü oluşturdum. if ler içerisinde ihtiyacım olan sınıfların klasörlerini oluşturdum 6 adet 
klasörüm olmuş oldu.

Gerekli .png'leri label kontrolü ile Train klasöründeki klasörlere kaydettim.

Gerekli .png'leri label kontrolü ile Train klasöründeki klasörlere kaydettim.

Bu işlemlerden sonra Train klasörünün içerisindeki her bir dosyada 500 adet görüntü Test klasörümün içerisindeki dosyalarda 100 adet görüntü hazır olarak bulunmakta.
Her klasöre ayrı ayrı girerek o klasörde bulunan bütün resimlerin başına sayısını ekledim. 

Örneğin tulip klasöründeki bütün resim adlarının başına 1 ekledim, sea klasöründeki resimlerinin adlarını başına 2 vb. Resimlerin her birinin hangi nesne olduğunu ifade edebilmek için label_img fonksiyonunu yazdım.

Bu fonksiyonda parametre olarak gönderilen resmin adında ilk objeye bakar ve eklediğim sayıları görmüş olur.
Gerekli return işlemini gerçekleştirir böylelikle hangi resim hangi sınıfa ait ayırmış oluyorum.

# MODEL

        • 5 konvolüsyon 
        • 3 dense katmanı kullanarak oluşturdum.
Aktivasyon fonksiyonu olarak relu seçtim, ancak son katmanda aktivasyon fonksiyonu olarak softmax 
seçtim.
6 adet resim sınıfım olduğu için son dense katmanın çıkışı 6 olarak belirlend

Model oluşturduktan sonra eğitim ve test verilerimin bulunduğu dizilerdeki verileri görüntü ve label 
olarak ayrılması gerekir bu işlem için Numpy kütüphanesi yardımı ile gerçekleştirdim.

Ardından eğitimi başlatmak için fit fonksiyonunu kullandım. Train görüntülerimin bulunduğu X değişkeni, Train labellarımın bulunduğu Y dizisini verdim. 
Validation olarak test verilerimi verdim. Batch_size olarak belirledim ve shuffle’ı TRUE olarak belirledim.

30. Epoch bir eğitim gerçekleşti. Ve val_acc: 0.7767 olarak hesaplandı.
Grafiklerin çizimi için matplotlip.pyplot kod bloğu kullanıldı.

![99](https://user-images.githubusercontent.com/61979226/136683001-cc14db46-b6d3-4b62-8be2-6622c11c51d5.png)


# DROPOUT

Dropout nöronlar arasında rastgele kesme işlemleri yaparak ağın başarı düzeyini artırmayı hedeflemektedir.
Yan tarafta dropoutların kullandığı ağ yapısı bulunmakta. Ağda 3 adet dropout kullanıldı.
Birinci ve ikinci dropout Konvolüsyon katmanında üçüncü dropout dense katmanında kullanıldı.

30. Epoch bir eğitim gerçekleşti. Ve val_acc: 0.7683 olarak hesaplanır.


![88](https://user-images.githubusercontent.com/61979226/136683032-370f61a9-2b55-4852-a9d0-4c61c97f070d.png)

# DATA AUGMENTİON

Veri zenginleştirme işleminin bir çok yöntemi bulunmaktadır örneğin , çevirme, yan yatırma, görüntülerin boyutları ile oynama, zoom yapma, renkleri ile oynama gibi işlemler yaparak veri çeşitliliğini artırarak modeli daha başarılı bir hale getirmeyi hedefler.
Bu projede rotation_range ve width_shift_range kullanıldı.
Model oluşturulup fit çalıştırdıktan sonra datagen.fit(X) X (train görüntülerini) datagen’e bağlar yani parametre olarak verilen işlemleri yapar.
Flow veri ve etiket dizileri alır bir de batch_size i verdim ve model.fit_generator çalıştırdım.

30. Epoch bir eğitim gerçekleşti. Ve val_acc:7883 olarak hesaplanır.

        *rotation_range resimleri rastgele rotasyonlar yapmak içindir. 
        *width_shift_range resmi kaydırma işlemi uygulamaktadır.

![77](https://user-images.githubusercontent.com/61979226/136683077-1f2a438f-2cd3-4553-aea8-8961cb605b7f.png)










