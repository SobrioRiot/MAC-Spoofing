من توضیح خواهم داد که چگونه این کار را برای هر مبتدی مثل من انجام دادم.
ابتدا نام دستگاه های رابط خود را از طریق دستور زیر بررسی کنید.
```
ip link show 
```
دستگاه اترنت با چیزی E شروع می شود دستگاه بی سیم با چیزی -W شروع می شود
و آدرس مک اصلی آن در کنار link/ether قرار می گیرد XX:XX:XX:XX:XX:XX:XX:XX:XX
سپس macchanger را نصب کنید
```
sudo apt install macchanger
```
می توانید MAC را از طریق *** تغییر دهید
```
sudo ifconfig <رابط> down

sudo ifconfig <رابط> down

sudo ifconfig <رابط> up
```

از اینجا، MacChanger نصب می‌شود و در صورت تمایل یک پنجره پیکربندی ظاهر می‌شود
MAC هر بار که دستگاه خود را راه اندازی مجدد می کنید یا هنگامی که رادیو وای فای را تشخیص می دهد. اصولاً گزینه تغییر خودکار MAC.
اگر می خواهید، <Enter> بله. اما بررسی کنید که آیا آدرس مک شما با راه اندازی مجدد دستگاه تغییر می کند یا خیر.

هنگام راه اندازی مجدد، اجرا کنید
```
ip link show 
```
همچنین در صورت نیاز به راحتی می توانید خطوط فرمان را پیدا کنید.
```
sudo macchanger -h (راهنما)
```
و بنابراین می توانید مک آدرس خود را هر زمان که نیاز داشته باشید تغییر دهید.
برای کسانی که نتوانستند پس از "بله"، macpoof کردن خود را خودکار کنند، این کاری است که من انجام دادم. اما اول....
شما باید سودو را در ابتدا قرار دهید
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
