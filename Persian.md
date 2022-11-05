من به شما توضیح خواهم داد که چگونه این کار را به راحتی انحام بدید حتی توسط افراد مبتدی، ابتدا نام دستگاه های شبکه ی خود را از طریق دستور زیر بررسی کنید.
```
ip link show 
```
دستگاه اترنت با کاراکتر E شروع می شود دستگاه بی سیم با کاراکترW شروع می شود و آدرس مک اصلی آن در کنار link/ether قرار می گیرد XX:XX:XX:XX:XX:XX:XX:XX:XX سپس macchanger را نصب کنید
```
sudo apt install macchanger 
```
* می توانید MAC را با این روش تغییر دهید*
```
sudo ifconfig <رابط> down sudo ifconfig <رابط> down sudo ifconfig <رابط> up 
```
از اینجا، MacChanger نصب می‌شود و در صورت تمایل یک پنجره پیکربندی ظاهر می‌شود MAC هر بار که دستگاه خود را راه ریستارت می کنید یا هنگامی که وای فای را تشخیص می دهد گزینه تغییر خودکار MAC را نمایش میدهد در صورتی که می خواهید استفاده کنید Yes را انتخاب کنید. اما بررسی کنید که آیا آدرس MAC شما با راه اندازی مجدد دستگاه تغییر می کند یا خیر.

پس از راه اندازی مجدد دستور زیر را اجرا کنید
```
ip link show 
```
همچنین در صورت نیاز به راحتی می توانید macmanager را در خطوط فرمان را پیدا کنید.
```
sudo macchanger -h (راهنما) 
```
و بنابراین می توانید MAC ADDRESS خود را هر زمان که نیاز داشته باشید تغییر دهید. برای کسانی که نتوانستند تغییر خودکار مک آدرس را پس از انتخاب گزینه "yes" فعال کنند این کاری است که من انجام دادم. اما ابتدا شما باید Sudo را در اول این دستور قرار دهید
```
sudo nano /etc/systemd/system/macspoof@.service 
```

سپس دقیقاً کپی و پیست کنید

```
Unit]

Description=macchanger on %I

Wants=network-pre.target

Before=network-pre.target

BindsTo=sys-subsystem-net-devices-%i.device

After=sys-subsystem-net-devices-%i.device

[Service]

ExecStart=/usr/bin/macchanger -e %I

Type=oneshot

[Install]

WantedBy=multi-user.target
```

خارج شوید و ذخیره کنید، سپس دستگاه های MAC خود را فعال کنید. من این کار را با رابط اترنت و بی سیم انجام دادم. به یاد داشته باشید که نام کارت شبکه را وارد کنید، با اولین دستور آن را دریافت می کنید.

```
sudo-i systemctl macspoof@<نام رابط اترنت شما>.service systemctl macspoof@<نام رابط بی سیم شما>.service 
```

**لطفاً <> را با دستگاه خود جایگزین کنید. مثال:

```
systemctl enable macspoof@<wlan0>.service 
```

سپس ریبوت کنید و آدرس مک خود را از طریق «ip link show» چک کنید.
```
Wants=network-pre.target

Before=network-pre.target

BindsTo=sys-subsystem-net-devices-%i.device

After=sys-subsystem-net-devices-%i.device

[Service]

ExecStart=/usr/bin/macchanger -e %I

Type=oneshot

[Install]

WantedBy=multi-user.target
```

خارج شوید و ذخیره کنید، سپس دستگاه های MAC خود را فعال کنید.
من این کار را با رابط اترنت و بی سیم انجام دادم.
به یاد داشته باشید که نام رابط را وارد کنید، با اولین دستور آن را دریافت می کنید.
```
sudo-i

systemctl macspoof@<نام رابط اترنت شما>.service

systemctl macspoof@<نام رابط بی سیم شما>.service
```
**لطفاً <> را با دستگاه خود جایگزین کنید.
مثال:
```
systemctl enable macspoof@<wlan0>.service
```
سپس ریبوت کنید و آدرس مک خود را از طریق «ip link show» تأیید کنید.
