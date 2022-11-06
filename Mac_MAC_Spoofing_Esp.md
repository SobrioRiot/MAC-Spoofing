Cómo cambiar la dirección MAC en Mac OS X

Falsificar la dirección MAC de los adaptadores AirPort en Mac OS X 10.4 (Tiger) y posteriores es bastante fácil. Sin embargo, 
por defecto, la dirección original se restablece tras el reinicio. En primer lugar, es posible que desee comprobar su dirección actual; 
escriba lo siguiente en una ventana de Terminal:
 
    ifconfig en1 | grep ether

Luego cambie la MAC con el siguiente comando:

    sudo ifconfig en1 ether xx-xx-xx-xx-xx-xx

Asegúrese de sustituir las x por la dirección que desee. Es posible que también tenga que cambiar el número de interfaz  
(en1) por otro. Puedes revisar las interfaces escribiendo ifconfig. La información de la dirección IP que aparece para cada interfaz 
puede darte una pista para distinguir entre ellas.

Si tienes problemas para que funcione, intenta desconectarte de todas las redes inalámbricas pero deja el adaptador AirPort encendido
y vuelve a intentarlo. Puedes forzarlo a hacer esto copiando y pegando el siguiente comando

    /Sistema/Librería/PrivateFrameworks/Apple80211.framework/Versiones/Actualidad/Recursos/airport /usr/sbin/airport -z
