![alt text](https://i.hizliresim.com/9jcl1yr.png)


**Sırasıyla Yapılması Gerekenler**

- **Node kurulumu**
- **Mds erişimi kontrolü**
- **Seeds ve mnemonicleri görüntüleme**
- **Backup oluşturma ve görüntüleme**
- **Mnemonic ve backup ile eski cüzdanı import etme**
- **Incentive Program Rewards uygulamasını Mds'ye yükleme**
- **Claim işlemi**


**Node kurulumu**

Halihazırda node'unuz varsa versiyon kontrolü yapın seeds-mnemonicleri yedekleyin. Backup alın ve geri kalan işlemleri yapın.

Eğer node kurulu değilse **https://testnet.run/minima** buradan docker ile kurulum yapabilirsiniz 
Kurulum yaparken MDS şifrenizi unutmayın. O şifre ile MDS erişimini sağlayacaksınız. (aşağıda gösterilen beyaz kutu olan yer)
![alt text](https://i.hizliresim.com/kn6vb78.png)

- **Mds erişimi kontrolü**

Node'un kurulu olduğu sunucunun Ip'si ile **https://sunucuipsi:9003/** buradan giriş yapın. Eğer sorun yaşıyorsanız ilk **https://sunucuipsi:9004/** adresinden güvenlik uyarısını kabul edin. Sonra tekrar 9003 olan linkten devam edin.

![alt text](https://i.hizliresim.com/4v8rx3x.png)

Bu ekranda Gelişmiş'e basıp ilerleyin.


![alt text](https://i.hizliresim.com/6hk9ftr.png)

Burada girecek olduğunuz şifre sunucuda belirlemiş olduğunuz (minima_mdspassword=123) şifredir. Şifreyi girdikten sonra Main Menu diyerek ilerleyin.
Eğer şifrenizi unutmuşsanız sunucu ana dizininde aşağıdaki kodları girerek ulaşabilirsiniz.
```
docker exec -it minima9001 /bin/sh
sh /bin/minima
```
```
mds
```
![alt text](https://i.hizliresim.com/nga8fvb.png)

MDS'ye tekrar dönmek üzere seeds ve mnemonic görüntülemeye geçelim.

**Seeds ve mnemonicleri görüntüleme**

Sunucuya tekrar giridğinizde ana dizine aşağıdaki kodu girdikten sonra vault yazın

```
docker exec -it minima9001 /bin/sh
sh /bin/minima
```

```
vault
```
![alt text](https://i.hizliresim.com/iu7atyj.png)

vault kodundan sonra çıkan mnemonicleri ve seeds'i bir yere kaydedin. 
locked:false yazmasının nedeni cüzdanınızın şifre ile kilitlenmemiş olduğundan dolayı.


**Backup oluşturma ve görüntüleme**

Backup uluşturmak için sh /bin/minima ile biten kodu yazmamışsanız ana dizinde iseniz.

```
docker exec -it minima9001 /bin/sh
sh /bin/minima
```

```
backup password: 
```
Eğer kodu direkt enter yaparsanız backup'ınız şifreli olarak saklanmaz. Şİfre koymak isterseniz backup password:'dan sonra şifrenizi yazıp kodu girin (şifre koymanıza gerek yok)

![alt text](https://i.hizliresim.com/gdhj95c.png)

Bacup'ınızı indirmek isterseniz Termius yada Winscp ile SFTP bağlantısı kurarak minimadocker9001 klasörünün içinden indirebilirsiniz.


![alt text](https://i.hizliresim.com/mrs30xa.png)

Her 24 saatte bir auto backup almasını isterseniz şu kodu girebilirsiniz.


```
backup auto:true 
```


- **Mnemonic ve backup ile eski cüzdanı import etme**

Önemli: 24 kelime (mnemonic) güvende tutun. Node'unuzu sadece bu kelimelerle kurtarabilirsiniz.
Terminal Minidapp içindeyken (sh /bin/minima olan kod)


```
vault action:restorekeys phrase:"24kelimeniziburayayazın"
```

![alt text](https://i.hizliresim.com/9255en0.png)

Backup'ı geri yüklemek için önceden almış olduğunuz minima-backup-xxxxxxx.bak dosyasını import etmek istediğiniz sunucuya SFTP ile bağlanarak minimadocker9001 klasörü içine yükleyin.

minima-backup-xxxxxxx.bak olan yere dosyanızın tam ismini girin. Eğer backup şifresi kullanmamışsanız koddan sonra direkt enter yapın.

```
backup file:minima-backup-xxxxxxx.bak password:
```

![alt text](https://i.hizliresim.com/k4squyu.png)


**Incentive Program Rewards uygulamasını Mds'ye yükleme**

**https://minidapps.minima.global/** sitesinden Incentive Program Rewards uygulama dosyasını indirin.

![alt text](https://i.hizliresim.com/r6e52wr.png)

MDS'ye giriş yapın (Mds erişimi kontrolü başlığında anlatıldı) ve en alttaki dosya seç yerinden indirdidğiniz dosyayı seçerek install yapın.

![alt text](https://i.hizliresim.com/sluriqt.png)

Uygulama doğru yüklendiğinde alttaki gibi görünecektir. Girmek için uygulamaya tıklayın.


![alt text](https://i.hizliresim.com/lwc4mab.png)

Gelen ekranda ödül bulunan mail ve incentive sitesindeki şifrenizi girin. Aşağıdaki gibi ödülünüz ve mailiniz gözükmesi gerek.

![alt text](https://i.hizliresim.com/t4gkue9.png)

Request Withdrawal'a basarak çekme talebinde bulunun

Kutucuk içinde yazan yazıya dikkat edin: Gösterilen Para Çekme Adresi, bu node'dan otomatik olarak oluşturulmuştur. Bu, 64 varsayılan adresinizden biridir ve Wallet MiniDapp'inizde gösterilen adresle eşleşmeyebilir.

![alt text](https://i.hizliresim.com/g9z14ma.png)

**İşlem tamamlandı. Bundan sonra yapmanız gerekenler;**

- **Çekim talebi bulunduğunuz cüzdan mnemoniclerini ve seeds'ini saklamak**
- **Eğer node'unuz çalışıyor durumda kalacaksa bile sık sık backup almak. Bunu yukarıdaki auto kodu ile yapabilirsiniz. Her 24 saatte bir backup alır**
- **Eğer node'unuzu kapatacaksanız en son aldığınız backup ile yeni kuracağınız zamanki aralık az olsun. İstenilen 2-3 haftada bir backup alınması**


**Nade'unuzu silmek istiyorsanız**

```
docker stop minima9001
docker rm minima9001
```
```
sudo rm -rf minimadocker9001
```


- **https://t.me/testnetrun**

- **https://t.me/minima_Turkey**

- **https://www.youtube.com/@TestNetRun**

- **https://testnet.run/**

- **https://stake.testnet.run/**

- **https://twitter.com/testnetrun**

![alt text](https://i.hizliresim.com/qw3rv2w.png)






