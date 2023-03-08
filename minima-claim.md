![alt text](https://i.hizliresim.com/i19z25m.png)

**Sırasıyla Yapılması Gerekenler**

- **Node kurulumu**
- **Mds erişimi kontrolü**
- **Seeds ve mnemonicleri görüntüleme**
- **Backup oluşturma ve görüntüleme**
- **Incentive Program Rewards 2.15.1 uygulamasını Mds'ye yükleme**
- **Claim işlemi**


**Node kurulumu**

#Eğer node kurulu değilse **https://testnet.run/minima** buradan docker ile kurulum yapabilirsiniz 
Kurulum yaparken MDS şifrenizi unutmayın. O şifre ile MDS erişimini sağlayacaksınız. (aşağıda gösterilen beyaz kutu olan yer)
![alt text](https://i.hizliresim.com/kn6vb78.png)

**Mds erişimi kontrolü**

#Node'un kurulu olduğu sunucunun Ip'si ile **https://sunucuipsi:9003/** buradan giriş yapın. Eğer sorun yaşıyorsanız ilk **https://sunucuipsi:9004/** adresinden güvenlik uyarısını kabul edin. Sonra tekrar 9003 olan linkten devam edin.

![alt text](https://i.hizliresim.com/4v8rx3x.png)

#Bu ekranda Gelişmiş'e basıp ilerleyin.


![alt text](https://i.hizliresim.com/6hk9ftr.png)

#Burada girecek olduğunuz şifre sunucuda belirlemiş olduğunuz (minima_mdspassword=123) şifredir. Şifreyi girdikten sonra Main Menu diyerek ilerleyin.
MDS'ye tekrar dönmek üzere seeds ve mnemonic görüntülemeye geçelim.

**Seeds ve mnemonicleri görüntüleme**

#Sunucuya tekrar giridğinizde ana dizine aşağıdaki kodu giridkten sonra vault yazın
```
docker exec -it minima9001 /bin/sh
sh /bin/minima
```

![alt text](https://i.hizliresim.com/iu7atyj.png)

#vault kodundan sonra çıkan mnemonicleri ve seeds'i bir yere kaydedin. 
locked:false yazmasının nedeni cüzdanınızın şifre ile kilitlenmemiş olduğundan dolayı.
