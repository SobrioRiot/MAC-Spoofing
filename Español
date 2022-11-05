# Explicare como lo hice para cualquier novato como yo.
 ------------------------------------------------------------------------------------------------

# Primero verifique el nombre de sus dispositivos de interfaz a través del siguiente comando

$ ip link show 

# El dispositivo Ethernet comienza con E algo El dispositivo inalámbrico comienza con -W algo 
# y su dirección mac original se coloca junto a link/ether XX:XX:XX:XX:XX:XX

> Luego instale macchanger

$ sudo apt install macchanger

# *** Podrías cambiar la MAC a través de ***

$ sudo ifconfig <interfaz> down

$ sudo macchanger -a <interfaz>

$ sudo ifconfig <interfaz> up


# Desde aquí, MacChanger se instalará y aparecerá una ventana de configuración si desea una nueva dirección 
# MAC cada vez que reinicie su dispositivo o cuando detecte la radio wifi. Básicamente, la opción automática de cambio de MAC 
# Si quieres entonces <Enter> en sí. Pero verifique si su dirección de Mac cambia cuando reinicia su dispositivo.

> Al reiniciar, ejecute 

$ ip link show 

# Además, si lo necesita, puede encontrar fácilmente las líneas de comando.

sudo macchanger -h (ayuda)

# Y asi puedes cambiar tu dirección MAC cuando lo necesites.

# Para aquellos que no pudieron automatizar su macpoofing después de "SÍ", esto es lo que hice. pero primero...

# DEBE PONER SUDO AL PRINCIPIO

sudo nano /etc/systemd/system/macspoof@.service

# luego copia y pega exactamente

---------------------------------------------------------------------------------------------------

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

----------------------------------------------------------------------------------------------------

# Salga y guarde, luego habilite sus dispositivos MAC. 
# Yo lo hice con la interfaz de Ethernet y la inalámbrica.
# Recuerda colocar el nombre de la interfaz, se obtiene con el primer comando.

$ sudo-i

 systemctl enable macspoof@<Nombre de su interfaz Ethernet>.service

 systemctl enable macspoof@<Nombre de su interfaz inalámbrica>.service

# **reemplace <> con su dispositivo, por favor 

> Ejemplo:

systemctl enable macspoof@<wlan0>.service

# Luego reinicie y verifique su dirección mac a través de "ip link show"
