# android_dz2

В приложении присутствует уязвимость связанная со сканером куар кода. После сканирования qr кода его содержимое попадает в логику программы.
![image](https://github.com/ambushidozho/android_dz2/assets/102957421/d3ce7e30-a9e3-4fc8-aa58-46a3240ab4e9)
Мы видим что в содержимое html страницы может попасть содержимое qr кода, для этого нужно лишь обойти checker и мы сможем исполнить любой js код
![image](https://github.com/ambushidozho/android_dz2/assets/102957421/d273e9c9-40e5-4c6b-9fbe-60c01b9bc532)
Для обхода чекера нам нужно лишь подобрать поле sign так чтобы хеш от поля promo + 12345 совпадал с sign
![image](https://github.com/ambushidozho/android_dz2/assets/102957421/5885f615-bf1d-4101-a69b-73b702125a4f)
Таким образом мы можем прокинуть вредоносный тег script на страницу и исполнить js. С помощью интерфейса получить токен юзера и отправить в любое место.
![image](https://github.com/ambushidozho/android_dz2/assets/102957421/9d006439-8a99-4334-a8e4-526a392207eb)
Чтобы все таки уязвимость сработала, нашу вредоносную строку нужно превратить в qr код и в случае скана пользователем наш payload пройдет все проверки и украдет токен
Пример PoC: {'promo':'<script>alert(Android.getToken());</script>','sign':'c4ad0112a4b7aad58385349d66426fb6'}
Base32 : PMTXA4TPNVXSOORHHRZWG4TJOB2D4YLMMVZHIKCBNZSHE33JMQXGOZLUKRXWWZLOFAUSSOZ4F5ZWG4TJOB2D4JZME5ZWSZ3OE45COYZUMFSDAMJRGJQTIYRXMFQWINJYGM4DKMZUHFSDMNRUGI3GMYRWE56Q====



