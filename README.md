- Las aplicaciones tienen variables que dependen del ambiente en el cuál las ejecutamos por ejemplo: Producción, Certificación, Integración o Desarrollo.
Por ejemplo:
Dirección de servicios
Usuarios
Imágenes
- También es normal que una única app se publique "n veces" con nombres diferentes, vamos a suponer que tu aplicación se llama: "com.miempresa.app". La empresa "ClienteA" y "ClienteB" te compran los ejecutables y solicitan publicarlos en el play store además firmas un contrato de mantenimiento y cada mejora debes actualizar el app para ambos clientes.
¿Tendríamos que renombrar el package o lo manejamos con branch diferentes?. Mejor serìa compilar el app, sin cambiar el packageName, con applicationId diferentes por ejemplo:
com.miempresa.app.ClienteA
com.miempresa.app.ClienteB
- Como podemos manejar la versión beta y full de un APP?
Para todo estas situaciones podemos usar "productFlavors". En el build.gradle del APP agregar lo siguiente:
productFlavors {
ClienteA {
minSdkVersion 14
targetSdkVersion 23
applicationId 'com.miempresa.app.clientea'
signingConfig signingConfigs.config
versionCode 1
versionName "1.0"
multiDexEnabled = true
}
ClienteB {
minSdkVersion 14
targetSdkVersion 23
applicationId 'com.miempresa.app.clienteb'
signingConfig signingConfigs.config
versionCode 1
versionName "1.0"
multiDexEnabled = true
}
TrialVersion {
minSdkVersion 14
targetSdkVersion 23
applicationId 'com.miempresa.app.trial'
signingConfig signingConfigs.config
versionCode 1
versionName "1.0"
multiDexEnabled = true
}
FullVersion {
minSdkVersion 14
targetSdkVersion 23
applicationId 'com.miempresa.app.clientex'
signingConfig signingConfigs.config
versionCode 1
versionName "1.0"
multiDexEnabled = true
}
}




![Alt text](https://raw.githubusercontent.com/mzegarras/ProductFlavors/master/1_AppsIcon.png "Optional Title")
![Alt text](https://raw.githubusercontent.com/mzegarras/ProductFlavors/master/2_AndroidStudio.png "Optional Title")


