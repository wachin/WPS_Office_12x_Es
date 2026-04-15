# WPS Office 12.x en español para Linux

Este repositorio sirve para poner **WPS Office 12.x** en **español** en Linux.

Aqui vas a encontrar dos cosas:

- `mui/`: archivos que traducen la interfaz del programa.
- `spellcheck/`: diccionarios para la correccion ortografica.

La idea es simple:

1. Instalas WPS Office.
2. Copias los archivos de idioma.
3. Cambias la configuracion para que WPS arranque en español.
4. Copias los diccionarios para que funcione el corrector ortografico.

## Que necesitas antes de empezar

- Tener **WPS Office 12.x** instalado.
- Tener permisos de administrador con `sudo`.
- Tener este repositorio descargado o clonado en tu computadora.
- Haber abierto **WPS Office al menos una vez**.

Importante:

- El archivo `~/.config/Kingsoft/Office.conf` normalmente **se crea cuando abres WPS por primera vez**.
- Si ese archivo no existe, abre WPS, cierralo, y luego continua con el tutorial.

## Que significa cada ruta

Si eres estudiante y estas empezando en Linux, esto te ayuda:

- `/opt/kingsoft/wps-office/office6/mui/`
  Aqui WPS guarda los archivos de idioma de la interfaz.
- `/opt/kingsoft/wps-office/office6/dicts/spellcheck/`
  Aqui WPS guarda los diccionarios del corrector ortografico.
- `~/.config/Kingsoft/Office.conf`
  Aqui WPS guarda la configuracion del usuario.

## Paso 1: instala WPS Office

Descarga el instalador de WPS Office para tu distribucion Linux.

Sitio oficial:

- [https://www.wps.cn](https://www.wps.cn)

Luego instala el paquete.

Si usas Debian, Ubuntu, Linux Mint o similares:

```bash
sudo dpkg -i wps-office*.deb
```

Si usas Fedora, Red Hat o similares:

```bash
sudo dnf install wps-office*.rpm
```

## Paso 2: copia los archivos del idioma español

Desde la carpeta de este repositorio, ejecuta:

```bash
sudo cp -r mui/* /opt/kingsoft/wps-office/office6/mui/
```

Que hace este comando:

- Copia `es_ES` y `es_MX` dentro de la carpeta de idiomas de WPS.
- Eso permite que WPS tenga disponibles los archivos de interfaz en español.

## Paso 3: cambia la configuracion para que WPS abra en español

Abre el archivo de configuracion del usuario:

```bash
nano ~/.config/Kingsoft/Office.conf
```

Borra lo que tenga y deja este contenido:

```ini
[General]
languages=es_ES

[6.0]
common\DefaultLanguage=3082
common\Local\UILanguage=3082
wpsoffice\Application%20Settings\AppComponentMode=prome_independ
wpsoffice\Application%20Settings\AppComponentModeInstall=prome_independ
```

Que hace esta configuracion:

- `languages=es_ES`
  Le dice a WPS que use español de España como idioma principal.
- `DefaultLanguage=3082` y `UILanguage=3082`
  Fuerzan la interfaz grafica en español.
- `AppComponentMode=prome_independ`
  Hace que WPS use el modo de ventanas que funciona mejor con esta configuracion.

Guarda el archivo en `nano` con:

1. `Ctrl + O`
2. `Enter`
3. `Ctrl + X`

## Paso 4: copia los diccionarios para la correccion ortografica

En este manual, los diccionarios se instalan en la ruta global de WPS dentro de `/opt`.

Desde la carpeta de este repositorio, ejecuta:

```bash
sudo cp -r spellcheck/* /opt/kingsoft/wps-office/office6/dicts/spellcheck/
```

Que hace este comando:

- Copia los diccionarios de español a la carpeta que usa WPS para revisar ortografia.
- Permite activar variantes como `es_ES`, `es_MX`, `es_EC`, etc.

## Paso 5: cierra y vuelve a abrir WPS Office

Si WPS estaba abierto, cierralo por completo y vuelve a iniciarlo.

Si todo salio bien:

- la interfaz aparecera en español
- el menu de correccion ortografica mostrara opciones de español

## Resultado esperado

Cuando termines, WPS deberia verse en español:

![imagen](https://github.com/user-attachments/assets/686b8367-afbb-4487-a999-e61eef9d74c7)

![imagen](https://github.com/user-attachments/assets/6898a1e5-2caf-48a8-9136-a05217f24906)

![imagen](https://github.com/user-attachments/assets/d5ea0f02-e6d9-4b36-a739-fabd37626cd3)

## Como activar la correccion ortografica en español

Despues de copiar los diccionarios, abre WPS Writer y revisa las opciones de idioma o correccion ortografica.

Las siguientes imagenes muestran la parte visual del proceso:

![imagen](https://github.com/user-attachments/assets/a297b315-32e8-42ba-a1cf-3d1383ac9a13)

![imagen](https://github.com/user-attachments/assets/ea83a4c3-27b0-4667-ac46-f00c28c77b0e)

## Si algo no funciona

Revisa estas 5 cosas:

1. Abriste WPS al menos una vez antes de editar `Office.conf`.
2. Copiaste `mui/*` en `/opt/kingsoft/wps-office/office6/mui/`.
3. Copiaste `spellcheck/*` en `/opt/kingsoft/wps-office/office6/dicts/spellcheck/`.
4. El archivo `Office.conf` quedo exactamente como aparece en este tutorial.
5. Cerraste y abriste WPS otra vez despues de hacer los cambios.

## Resumen rapido

Si ya entendiste el proceso y solo quieres los comandos:

```bash
sudo cp -r mui/* /opt/kingsoft/wps-office/office6/mui/
sudo cp -r spellcheck/* /opt/kingsoft/wps-office/office6/dicts/spellcheck/
nano ~/.config/Kingsoft/Office.conf
```

Contenido de `Office.conf`:

```ini
[General]
languages=es_ES

[6.0]
common\DefaultLanguage=3082
common\Local\UILanguage=3082
wpsoffice\Application%20Settings\AppComponentMode=prome_independ
wpsoffice\Application%20Settings\AppComponentModeInstall=prome_independ
```

Si este tutorial te ayudo, puedes dejar una estrella en el repositorio.
