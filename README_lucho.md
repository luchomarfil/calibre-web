

## test local  ---  levantar el venv (ver manual-instalattion)
./venv/bin/python3 -m pip install -r requirements.txt
./venv/bin/python3 cps.py
http://localhost:8083/?data=root&sort_param=stored

#Para elaborar todo el circuito se requiere de este repo y del repo de docker-calibre-web
* Pasos en este remo /luchomarfil/calibre-web
*) Commit y push de calibre web
*) Crear la release de calibre-web en Github y 
*) Regenerar el tag de docker-calibre-web que es el que chupa calibre-web
git tag -a "20240401" -m "20240401"
git push origin "20240401"
* Pasos con el repo docker-calibre-web. 
* parados en ese repo y con el tag creado, entonces
*) Docker build de la version
luchomarfil/soft:docker-calibre-web-20240401
*) probamos la imagen
*)Docker push de docker-calibre-web


Aquí está el texto ordenado de manera más clara y presentable:

---

## Configuración del circuito entre "calibre-web" y "docker-calibre-web"

Para establecer el circuito completo, se necesita trabajar tanto en el repositorio "calibre-web" como en el repositorio "docker-calibre-web".

### Pasos en el repositorio "/luchomarfil/calibre-web":

1. **Commit y Push de Calibre-Web**:
   - Realiza los cambios necesarios en el código de Calibre-Web.
   - Ejecuta los siguientes comandos:
     ```bash
     git add .
     git commit -m "Descripción del commit"
     git push origin tu_rama
     ```

2. **Crear la Release de Calibre-Web en GitHub**:
   - Crea una nueva release en GitHub con la versión correspondiente.

3. **Regenerar el Tag en docker-calibre-web**:
   - En el repositorio "docker-calibre-web":
     ```bash
     git tag -a "20240401" -m "20240401"
     git push origin "20240401"
     ```

### Pasos en el repositorio "docker-calibre-web":
0. **Mergear el fork externo con la nueva version si se desea**

1. **Docker Build de la versión**:
   - Con el tag creado, dirígete al repositorio "docker-calibre-web" y ejecuta:
     ```bash
     docker build -t luchomarfil/soft:docker-calibre-web-20240401 .
     ```

2. **Probar la Imagen**:
   - Antes de continuar, asegúrate de probar la imagen localmente para verificar su funcionamiento.

3. **Docker Push de docker-calibre-web**:
   - Finalmente, realiza el push de la imagen Docker al registro correspondiente:
     ```bash
     docker push luchomarfil/soft:docker-calibre-web-20240401
     ```

---

Este formato estructurado y claro presenta los pasos necesarios para configurar el circuito entre "calibre-web" y "docker-calibre-web" de manera más legible y comprensible.
