# Set-SSL-Certificate
How to set ssl in my website 

- How to add ssl free certificate to your website
- ဒိအပိုင်းမှာ ဆိုရင်တော့ မိမိ ကိုယ် ပိုင် website တစ်ခုမှာ ssl certificate ဘယ်လို ထည့်ရမလဲ ဆို တာကို ပြောပြသွားမှာ 
- Step 1
- Ubuntu server တစ်ခု နဲ့ project setup ေတာ့ လုပ်ထားရမှာ ပေါ့ေနာ်
- Step 2
- SSH ကနေ Root user အ နေနဲ့ ဝင်လိုက် ပါ့မယ်။
- ပီးတာနဲ့ sudo apt-get update ဆိုပီး ရိုက်လိုက်ပါ့မယ်
- Certbot plugin ကို  ဒိ command ကို သုံးပီ apache server ပေါ်မှာ install  ပါ့မယ်
- sudo apt-get install certbot python3-certbot-apache
- Step 3
- ဒီ command ကို သုံးပီးတော့ မိမိ domain name certificate ထုတ်ပါ့မယ်
- sudo certbot --apache -d your_domain.com
- တကယ် လို့ အောင်မြင်တယ်ဆိုရင်တော့ /etc/letsencrypts ဆိုတဲ့  folder အောက်မှာ မိိမိ  domain nameနဲ့ folder တစ်ခု တွေ့ရပါလိမ့် မယ်။
- /etc/letsencrypt/live/waiphyohlaing.com
- Step 3 
- ပီးရင်တော့ apache server ကို restart ချလိုက်ပါ့မယ်
- sudo systemctl restart apache2
- Step 4
- Auto renewal လုပ်ချင်တာဘဲ ဖစ်ဖစ် certificate valid ဖစ်မဖစ် သိချင်တာဘဲ ဖစ်ဖစ် ဒီ command ကို run ပေးလိုက်ပါ။
- sudo certbot renew --dry-run
- ဒါဆိုရင်တော့ certificate ထုတ်တဲ့ အပိုင်းအောင်မြင်ပါပီ

SetUp config ssl certificate
 
- /etc/apache2/site-avaliables ဆိုတဲ့ folder ထဲမှာ မိမိ domain name နဲ့ config file တစ်ခုတည် ဆောက်လိုက်ပါ။
- ဉပမာ - waiphyohlaing.config
-  ပီးရင် တော့ ဒိဟာကို copy ကူးပီး paste ချလိုက်ပါ
- ServerAlias waiphyohlaing.com
- SSLCertificateFile /etc/letsencrypt/live/yourdomain/fullchain.pem
- SSLCertificateKeyFile /etc/letsencrypt/live/yourdomain/privkey.pem
- SSLCertificateChainFile /etc/letsencrypt/live/yourdomain/chain.pem
- ဒီ Command ကို သုံးပီ config file ကို enable လုပ် ပေးပါ
- sudo a2enmod ssl
- sudo apache2ctl configtest
-  Apache server ကို ဒီ command သုံးပီ restart ချလိုက်ပါ
- sudo systemctl restart apache2
- အဆင့်တွေ ပီးသွားရင် ကျွန် တော်တို့ website ကို ssl ထည့်တာ အောင်မြင်တယ် လို့ ပြောလို့ ရပါပီ။
- အခုလို လာရောက်ဖတ် ပေးတဲ့ အတွက် ကျေးဇူးတင်ပါတယ်။
