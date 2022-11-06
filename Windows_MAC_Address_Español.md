Los adaptadores de red vienen preconfigurados de fábrica con su propia dirección física o de control de acceso al medio (MAC), única en el mundo,
que les ayuda a identificarse cuando se comunican con otros componentes de red. 
Aunque no puede cambiar la dirección MAC permanente que almacena realmente el adaptador de red 
puede hacer que proporcione una dirección diferente utilizando su sistema operativo (OS). Veremos cómo hacer esto con Windows.

Hay algunas razones por las que puede querer simular otra dirección MAC, incluyendo la resolución de problemas y la prueba de su red. 
Desde el punto de vista de la seguridad, es una buena idea entender la técnica, conocida como "MAC spoofing", porque los hackers también la encuentran
útil para evitar el filtrado de direcciones MAC. Este filtrado es utilizado por algunos administradores de red para ayudar a controlar los dispositivos
que los usuarios finales pueden conectar a la red o incluso como otra capa de seguridad contra los hackers. Aunque sólo sea por eso, entender el 
MAC spoofing te ayudará a demostrarte a ti mismo o a los demás lo fácil que es es cambiar tu dirección y eludir las medidas de seguridad basadas 
en la MAC.


# Cambiar la dirección MAC en Windows

Antes de cambiar la dirección MAC, es posible que quieras anotar la original. Una forma de hacerlo es abrir la ventana de Conexiones de Red, 
hacer doble clic en el adaptador de red deseado, y en la ventana de Estado de la Conexión de Red, hacer clic en el botón 
Detalles para buscar la Dirección Física. 
Otra forma es abrir un símbolo del sistema, escribir ipconfig /all, encontrar la conexión de red deseada y buscar la dirección física.

La forma más fácil de cambiar la dirección MAC en Windows es a través de las Propiedades del Adaptador de Red. Probablemente quiera probar esto primero, 
dejando el método del Registro como último recurso. Cuando esté listo, inténtelo:


  > Abra la ventana de Conexiones de Red y haga doble clic en el adaptador de red deseado.
    En la ventana Estado de la conexión de red, haga clic en el botón Propiedades.
    En la ventana Propiedades de la conexión de red, haga clic en el botón Configurar.
    En la ventana de Propiedades del Adaptador de Red, seleccione la pestaña Avanzado.
    Elija la propiedad Dirección de red o Dirección administrada localmente, 
    seleccione el botón de opción Valor y, a continuación, introduzca la nueva dirección MAC. 
    Si utiliza Windows 7, debe utilizar un formato especial como veremos en un momento. 
    Haga clic en Aceptar para guardar los cambios.

Si no tiene éxito al cambiar su MAC a través de las Propiedades del Adaptador de Red, puede intentar utilizar el Registro de Windows.
Sin embargo, primero debes copiar la dirección original antes de proceder para tenerla si quieres restaurarla. 
Cuando estés listo, aquí tienes cómo editar la configuración del Registro de Windows 
de Windows:


   >Abra el Editor del Registro escribiendo regedit en el campo del menú de inicio o en el indicador de ejecución.
    Busque la siguiente clave: 
    HKEY_LOCAL_MACHINESYSTEMCurrentControlSetControlClass{4D36E972-E325-11CE-BFC1-08002BE10318}
    Debería ver subclaves de 4 dígitos, como 0000, 0001, 0002, 0003, etc. 
    Encuentre el adaptador de red correcto consultando el atributo DriverDesc 
    de cada subclave.
    Una vez que encuentre el adaptador deseado, vea si contiene un atributo NetworkAddress. 
    Si no es así, cree una nueva cadena (REG_SZ) y 
