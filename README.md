gradle-mvn-push
===============

Clon de: [https://github.com/chrisbanes/gradle-mvn-push/](https://github.com/chrisbanes/gradle-mvn-push).


## Uso

Versión simplificada.

### 1. Establecer la propiedades generales (home - gradle.properties)

Localización por defecto:
`USER_HOME/.gradle/gradle.properties`.

```properties
NEXUS_USERNAME=development
NEXUS_PASSWORD=ZZZ

signing.keyId=YYY
signing.password=XXX
signing.secretKeyRingFile=~/.gnupg/secring.gpg
```

Para generar la firma, puedes utilizar PGP Tools (mac brew install -v gpg).

```
gpg --gen-keys
hph --list-keys
```
Donde YYY es:

```
pub ABDC/YYY 2014-05-01 Jose Gil <jose.gil@uji.es>
```



### 2. Establecer las propiedades del módulo a desplegar (módulo - gradle.properties)

```properties
VERSION_NAME=1.0.1
VERSION_CODE=2
GROUP=es.uji.geotec

POM_NAME=UJI Opendata Android library
POM_ARTIFACT_ID=uji-opendata
POM_PACKAGING=AAR

POM_DESCRIPTION=UJI Opendata Android library
POM_URL=https://github.com/GeoTecINIT/uji-opendata-android
POM_SCM_URL=https://github.com/GeoTecINIT/uji-opendata-android
POM_SCM_CONNECTION=scm:git@github.com:GeoTecINIT/uji-opendata-android.git
POM_SCM_DEV_CONNECTION=scm:git@github.com:GeoTecINIT/uji-opendata-android.git
POM_LICENCE_NAME=The Apache Software License, Version 2.0
POM_LICENCE_URL=http://www.apache.org/licenses/LICENSE-2.0.txt
POM_LICENCE_DIST=repo
POM_DEVELOPER_ID=jose-gil
POM_DEVELOPER_NAME=Jose Gil

RELEASE_REPOSITORY_URL=http://geo4.dlsi.uji.es:8081/content/repositories/releases/
SNAPSHOT_REPOSITORY_URL=http://geo4.dlsi.uji.es:8081/content/repositories/snapshots/
```

### 3. Aplicar la llamada al script (módulo - build.gradle)

Add the following at the end of each `build.gradle` that you wish to upload:

```groovy
apply from: 'https://raw.githubusercontent.com/jose-gil/gradle-mvn-push/master/gradle-mvn-push.gradle'
```

### 4. Compilar y subir


```bash
$ gradle clean build uploadArchives
```
	

## Licencía

    Copyright 2013 Chris Banes

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
